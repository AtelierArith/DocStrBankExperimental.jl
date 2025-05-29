```
isinexact(x::Floatmu{szE,szf}) where {szE,szf}
```

Return `true` if the value `x` was rounded when created as a `Floatmu{szE,szf}` and  `false` otherwise.

An NaN is never inexact. An infinite is inexact only if created from a finite value.

# See:

  * [`errorsign(x::Floatmu{szE,szf}) where {szE,szf}`](@ref).
  * [`reset_inexact()`](@ref)
  * [`inexact()`](@ref)

# Examples

```jldoctest
julia> isinexact(Floatmu{2, 2}(0.25)+Floatmu{2, 2}(2.0))
true
julia> isinexact(Floatmu{2, 2}(0.25)+Floatmu{2, 2}(1.5))
false
```
