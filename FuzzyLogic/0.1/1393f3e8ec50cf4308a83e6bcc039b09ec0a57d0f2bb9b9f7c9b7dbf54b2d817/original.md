```julia
struct SemiEllipticMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Semi-elliptic membership function.

### Fields

  * `cd::Real`: center.
  * `rd::Real`: semi-axis.

### Example

```julia
mf = SemiEllipticMF(5.0, 4.0)
```
