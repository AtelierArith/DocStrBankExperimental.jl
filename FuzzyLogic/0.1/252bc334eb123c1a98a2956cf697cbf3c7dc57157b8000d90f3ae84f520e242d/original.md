```julia
struct SigmoidMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Sigmoid membership function $\frac{1}{1+e^{-a(x-c)}}$.

### Fields

  * `a::Real`: parameter controlling the slope of the curve.
  * `c::Real`: center of the slope.

### Example

```julia
mf = SigmoidMF(2, 5)
```
