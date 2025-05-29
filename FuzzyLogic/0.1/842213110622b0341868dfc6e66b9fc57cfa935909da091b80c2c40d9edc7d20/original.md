```julia
struct GeneralizedBellMF{T<:Real, S<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Generalized Bell membership function $\frac{1}{1+\vert\frac{x-c}{a}\vert^{2b}}$.

### Fields

  * `a::Real`: Width of the curve, the bigger the wider.
  * `b::Real`: Slope of the curve, the bigger the steeper.
  * `c::Real`: Center of the curve.

### Example

```julia
mf = GeneralizedBellMF(2, 4, 5)
```
