This is a debian package which will take a base Ubuntu install (tested on Precise) and turn it into a fully-functional rutorrent server.

It will install rtorrent, apache, and php from the Ubuntu repos as dependencies, and then it clone rutorrent via git over HTTPS (thus making sure there is no unsigned code going through the network). Then it will add users, and set permissions on a couple of files it needs. Most of this is done in debian/postinst.

Note that this configuration is tuned for my home setup, which SCP's completed downloads to a fileserver. If you don't use this feature, you can simply ignore it (don't worry, it won't send your downloads to me!), but to be clean you can remove the bottom line in rtorrent.rc.skel. There's also a message on the install to remind you to generate keys for this SCP operation - you can ignore this if you aren't using it.

A note on security - we use a localhost-bound port to communicate between rtorrent and rutorrent. If your machine has naughty users on it, they may be able to bind to it (it is port 5000, so unprivileged). You might want to switch to using UNIX domain sockets instead if this is the case.

rtorrent is spawned in a new VT at the console, btw.

Please let me know if it works, or doesn't, for you!
