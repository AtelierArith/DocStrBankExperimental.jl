```
function ZeroValue(::Nothing)
function ZeroValue(units::Vector{Unitful.FreeUnits{N, D, nothing} where D where N} = uAstro)
```

Construct an immutable struct providing zero `Measurement` values in corresponding `units` (default is `uAstro`). Use `nothing` if unitless. Useful for accumulated summation, array initialization, etc.

# Examples

```
ZeroValue(nothing)
ZeroValue()
ZeroValue(uSI)
ZeroValue(uCGS)
```
