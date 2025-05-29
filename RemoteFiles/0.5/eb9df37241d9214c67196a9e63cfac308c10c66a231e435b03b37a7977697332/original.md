```
download(rfs::RemoteFileSet;
    quiet::Bool=false, verbose::Bool=false, force::Bool=false)
```

Download all files contained in `rfs`.

  * `quiet`: Do not print messages.
  * `verbose`: Print all messages.
  * `force`: Force download and overwrite existing files.
  * `force_update`: Overwrite existing files even if they are equal.
