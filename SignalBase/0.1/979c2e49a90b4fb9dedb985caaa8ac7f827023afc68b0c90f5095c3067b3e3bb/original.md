```
inradians([Type],x)
```

Given an angle value, convert to a value of Type (defaults to Float64) in radians. Unitless numbers are assumed to be in radians and are silently passed through.

## Examples

```jldoctest
julia> inradians(180°)
3.141592653589793

julia> inradians(2π)
6.283185307179586

julia> inradians(0.5π*rad)
1.5707963267948966
```
