```
folder_path(folder::String, root::String, folderatetype::String=""; make=false)
```

Returns the full path for a given folder, optionally creating the path if it does not exist.

# Arguments

  * `folder`: A folder name.
  * `root`: The root directory.
  * `foldertype`: The type of folder (optional, default is an empty string).
  * `make`: A boolean flag indicating whether to create the path if it does not exist (optional, default is `false`).

# Returns

  * `String`: The full path for the given folder.
