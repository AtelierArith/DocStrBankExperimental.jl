```
write_mesh(m :: TriMesh, file_name :: String; <keyword arguments>)
```

Write mesh to disk.

# Arguments

  * `file_name :: String`: Provide a string with path and filename

# Keyword arguments

  * `format :: String = "triangle"`: Specify mesh format. Only option for now is `"triangle"` (Triangle's native mesh format)
