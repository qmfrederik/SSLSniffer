SSLSniffer
==========

SSLSniffer is a DTrace script for socket communication sniffing with SSL
support.

Initially based on a script from pumpkin, but completely rewritten
to intercept messages at the SSL command level instead of the CoreFoundation
level (which therefore only dumped plist-based messages using the standard
CF API functions). 

Intercepting at the SSL level directly is a little bit bitchy because of
many tail-calls.

Also this version doesn't dump hex yet, only asciis. Dumping hexdump
without extra large output might be a little bit tricky (I'm not a dtrace
wizard) because dtrace's output print size is fixed, so you would always
have to print out the same amout of byte, even when there are less bytes in
the packet.

There are probably bugs or possible improvements to be made, feel free
to mail me patches.

Usage
=====

Usage example: sudo SSLSniffer.d -p <pid> or sudo SSLSniffer.d -c /path-to
By the way, if you want to attach to iTunes, you will need the
pt_deny_attach kext available at http://landonf.bikemonkey.org/code/macosx
