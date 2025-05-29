```
read_ball_ini_file(fname::AbstractString, ::Type{T} = Float32) -> BALLIniFile
```

Read a file in BALL's old Ini file format and return it as a BALLIniFile.

# Supported keyword arguments

  * `cleanup_keys::Bool = true` simplifies colon-separated key names (e.g., `ver:version` becomes `version`, `key:I` becomes `I`, etc.)
