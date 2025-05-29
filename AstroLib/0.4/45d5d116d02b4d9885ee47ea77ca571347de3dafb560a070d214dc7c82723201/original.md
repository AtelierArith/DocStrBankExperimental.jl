```
sixty(number) -> [deg, min, sec]
```

### Purpose

Converts a decimal number to sexagesimal.

### Explanation

The reverse of `ten` function.

### Argument

  * `number`: decimal number to be converted to sexagesimal.

### Output

An array of three `AbstractFloat`, that are the sexagesimal counterpart (degrees, minutes, seconds) of `number`.

### Example

```jldoctest
julia> using AstroLib

julia> sixty(-0.615)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
 -0.0
 36.0
 54.0
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
