```
read_tles(tles::AbstractString; verify_checksum::Bool = true) -> Vector{TLE}
```

Parse a set of TLEs in the string `tles`. This function returns a `Vector{TLE}` with the parsed TLEs.

# Keywords

  * `verify_checksum::Bool`: If `true`, the checksum of both TLE lines will be verified.   Otherwise, the checksum will not be checked. (**Default** = `true`)
