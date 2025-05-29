```
@tle_str(str) -> TLE
```

Parse one TLE in the string `str.

This function returns the parsed TLE or `nothing`, if an error occured.

!!! note
    This function verifies the checksums of the TLE. If the checksum verification is not desired, use [`@tle_nc_str`](@ref).


!!! note
    `str` must contain **only** one TLE. Hence, it must have two or three non-empty lines. The lines beginning with the character `#` are discarded.


# Example

```julia-repl
julia> tle = tle"""
       CBERS 4
       1 40336U 14079A   18166.15595376 -.00000014  00000-0  10174-4 0  9993
       2 40336  98.4141 237.7928 0001694  75.7582 284.3804 14.35485112184485
       """
```
