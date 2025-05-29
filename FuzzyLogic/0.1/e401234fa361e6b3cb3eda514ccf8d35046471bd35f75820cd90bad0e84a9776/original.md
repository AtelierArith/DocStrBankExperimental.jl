```julia
struct ProductSigmoidMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Product of two sigmoids. See also [`SigmoidMF`](@ref).

### Fields

  * `a1::Real`: slope of the first sigmoid.
  * `c1::Real`: center of the first sigmoid.
  * `a2::Real`: slope of the second sigmoid.
  * `c2::Real`: center of the second sigmoid.

### Example

```julia
mf = ProductSigmoidMF(2, 3, -5, 8)
```
