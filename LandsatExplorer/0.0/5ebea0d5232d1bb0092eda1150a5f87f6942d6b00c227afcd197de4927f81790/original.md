```
download_scene(scene, dir=pwd(); log_progress=true, unpack=false)
```

Download a Landsat scene and save to the given directory.

# Parameters

  * `scene`: The display name or entity ID of the scene to be downloaded.
  * `dir`: The directory in which to save the downloaded scene.

# Keywords

  * `unpack`: If true, unpacks and deletes the downloaded tar file (default = false).
  * `log_progress`: If true, logs the download progress at 1-second intervals (default = true).

# Returns

The path to the downloaded file(s).
