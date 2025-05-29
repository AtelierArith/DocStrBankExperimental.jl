```
dbc_send_file(path::AbstractString, filename = nothing; type = nothing)
```

Convert a file into the format expected by the Download component.

# Arguments

  * `path` - path to the file to be sent
  * `filename` - name of the file, if not provided the original filename is used
  * `type` - type of the file (optional, passed to Blob in the javascript layer)
