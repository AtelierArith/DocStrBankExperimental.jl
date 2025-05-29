```
@hms_str
```

Parse a string in `"ha:min:sec"` format directly to an angle. By default, it will be parsed as radians, but the angle can be chosen by adding a flag to the end of the string

  * `hms"..."rad` -> radians (default)
  * `hms"..."deg` -> degrees
  * `hms"..."ha` -> hour angles

# Examples

```jldoctest
julia> hms"12:17:25.3"
3.2176090147193626

julia> hms"12:17:25.3"rad # default
3.2176090147193626

julia> hms"12:17:25.3"deg
184.35541666666666

julia> hms"12:17:25.3"ha
12.29036111111111
```

# See also

[`parse_hms`](@ref)
