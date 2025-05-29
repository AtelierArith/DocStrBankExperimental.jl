```
FileSource(url::String, hash::String; filename::String = basename(url))
```

Specify a remote file to be downloaded from the Internet from `url`.  `hash` is the 64-character SHA256 checksum of the file.

In the builder environment, the file will be saved under `${WORKSPACE}/srcdir` with the same name as the basename of the originating URL, unless the the keyword argument `filename` is specified.
