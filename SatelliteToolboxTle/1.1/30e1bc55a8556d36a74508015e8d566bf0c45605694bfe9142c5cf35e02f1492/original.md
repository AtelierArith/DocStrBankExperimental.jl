```
read_tle(str::AbstractString; verify_checksum::Bool = false) -> TLE
```

Read the TLE in the string `str`.

!!! note
    `str` must contain **only** one TLE. Hence, it must have two or three non-empty lines. The lines beginning with the character `#` are discarded.


# Keywords

  * `verify_checksum::Bool`: If `true`, the checksum of both TLE lines will be verified.   Otherwise, the checksum will not be checked. (**Default** = `true`)
