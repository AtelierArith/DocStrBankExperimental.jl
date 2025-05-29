```
download_scene(scene, dir=pwd(); unzip=false, log_progress=true, access_token=nothing)
```

Download the requested Sentinel scene using the provided access token.

# Parameters

  * `scene`: The name of the jentinel scene to download.
  * `dir`: The destination directory of the downloaded scene (default = pwd()).

# Keywords

  * `unzip`: If true, unzips and deletes the downloaded zip file (default = false).
  * `log_progress`: If true, logs the download progress at 1-second intervals (default = true).
  * `access_token`: A token to authenticate the request. Calls `get_access_token()` if `nothing` (default).
