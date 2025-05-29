```
read_tles_from_file(filename::String; verify_checksum::Bool = true) -> Vector{TLE}
```

Read the TLEs in the file `filename` and return a `Vector{TLE}` with the parsed TLEs.

# Keywords

  * `verify_checksum::Bool`: If `true`, the checksum of both TLE lines will be verified.   Otherwise, the checksum will not be checked. (**Default** = `true`)
