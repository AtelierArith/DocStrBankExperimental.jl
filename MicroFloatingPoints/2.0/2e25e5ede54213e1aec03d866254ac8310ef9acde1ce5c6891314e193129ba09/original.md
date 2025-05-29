```
errorsign(x::Floatmu{szE,szf}) where {szE,szf}
```

Return `1` if `x` was rounded by excess when created as a `Floatmu{szE,szf}`, `-1` if it was rounded by default, and `0` if no rounding took place.

An NaN is never in error. An infinite is in error only if created from a finite value.

# See

  * [`isinexact(x::Floatmu{szE,szf}) where {szE,szf}`](@ref)
  * [`reset_inexact()`](@ref)
  * [`inexact()`](@ref)

# Examples

```jldoctest
julia> errorsign(Floatmu{2, 2}(0.5))
0
julia> errorsign(Floatmu{2, 2}(1.7))
1
julia> errorsign(Floatmu{2, 2}(-2.8))
-1
```
