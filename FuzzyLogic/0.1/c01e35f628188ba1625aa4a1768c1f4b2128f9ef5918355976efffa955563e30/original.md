```julia
struct LinearMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Linear membership function. If $a < b$, it is increasing (S-shaped), otherwise it is decreasing (Z-shaped).

### Fields

  * `a::Real`: foot.
  * `b::Real`: shoulder.

### Example

```julia
mf = LinearMF(2, 8)
```
