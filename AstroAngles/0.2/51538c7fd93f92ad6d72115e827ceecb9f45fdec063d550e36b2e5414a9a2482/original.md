```
@dms_str
```

Parse a string in `"deg:arcmin:arcsec"` format directly to an angle. By default, it will be parsed as radians, but the angle can be chosen by adding a flag to the end of the string

  * `dms"..."rad` -> radians (default)
  * `dms"..."deg` -> degrees
  * `dms"..."ha` -> hour angles

# Examples

```jldoctest
julia> dms"12:17:25.3"
0.21450726764795752

julia> dms"12:17:25.3"rad # default
0.21450726764795752

julia> dms"12:17:25.3"deg
12.29036111111111

julia> dms"12:17:25.3"ha
0.8193574074074074
```

# See also

[`parse_dms`](@ref)
