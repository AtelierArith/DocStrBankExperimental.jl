```
ArchiveSource(url::String, hash::String; unpack_target::String = "")
```

Specify a remote archive in one of the supported archive formats (e.g., TAR or ZIP balls) to be downloaded from the Internet from `url`.  `hash` is the 64-character SHA256 checksum of the file.

In the builder environment, the archive will be automatically unpacked to `${WORKSPACE}/srcdir`, or in its subdirectory pointed to by the optional keyword `unpack_target`, if provided.
