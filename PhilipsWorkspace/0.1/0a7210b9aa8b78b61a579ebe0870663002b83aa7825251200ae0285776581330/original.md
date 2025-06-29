```
read_workspace(path_to_workspace_file::String)
```

Reads a workspace from a JSON file that is exported using the UMCU Raw Export Tool patch.

# Arguments

  * `path_to_workspace_file::String`: The path to the workspace file. The function will remove any file extension from the path and append `.json`.

# Returns

  * `workspace`: A `Workspace` object that represents the workspace read from the file. All integers in the workspace are replaced with their corresponding enumeration values.

# Example

```
workspace = read_workspace("/path/to/workspace")
```
