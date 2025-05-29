```
download_scenes(scenes, dir=pwd(); unzip=false, access_token=nothing)
```

Download multiple scenes in parallel.

The number of parallel downloads is determined by `Threads.nthreads()`.

# Parameters

  * `scenes`: A list of scenes to download.

# Keywords

  * `dir`: The destination directory of the downloaded scene (default = pwd()).
  * `unzip`: If true, unzips and deletes the downloaded zip file (default = false).
  * `access_token`: A token to authenticate the request. Calls `get_access_token()` if `nothing` (default).
