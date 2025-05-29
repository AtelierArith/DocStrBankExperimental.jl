```
read_tle(l1::AbstractString, l2::AbstractString; kwargs...) -> TLE
```

Read the TLE in which the first line is `l1` and second line is `l2`.

# Keywords

  * `name::AbstractString`: The satellite name in the returned TLE object.   (**Default** = "UNDEFINED")
  * `verify_checksum::Bool`: If `true`, the checksum of both TLE lines will be verified.   Otherwise, the checksum will not be checked. (**Default** = `true`)
