```
write_torfile(fname::AbstractString, obj::TorObj; modestr = "w")
write_torfile(fname::AbstractString, objs::Vector{TorObj}; modestr = "w")
```

Write one or multiple `TorObj` objects to a Ticra-compatible TOR (Ticra Object Repository) file. With the default value of `modestr = "w"`, the file is created if it doesn't already exist, or, if it  already exists, it is truncated to zero length before writing the TOR object(s). By setting the value of `modestr` to `"a"` one can append the object(s) to an existing file.
