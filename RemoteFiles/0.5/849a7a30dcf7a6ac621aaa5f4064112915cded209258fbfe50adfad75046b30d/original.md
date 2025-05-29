```
download(rf::RemoteFile;
         quiet::Bool=false,
         verbose::Bool=false,
         force::Bool=false,
         retries::Int=0)
```

Download `rf`.

  * `quiet`: Do not print messages.
  * `verbose`: Print all messages.
  * `force`: Force download and overwrite existing files.
  * `force_update`: Overwrite existing files even if they are equal.
  * `retries`: Override the number of retries in `rf` if `retries != 0`
