```
folder_path(folder::Vector, root, foldertype)
```

Returns the full paths for a list of folders, optionally creating the paths if they do not exist.

# Arguments

  * `folders`: A list of folder names.
  * `root`: The root directory.
  * `foldertype`: The type of folder (optional, default is an empty string).
  * `make`: A boolean flag indicating whether to create the paths if they do not exist (optional, default is `false`).

# Returns

  * `Vector{String}`: The full paths for the given folders.
