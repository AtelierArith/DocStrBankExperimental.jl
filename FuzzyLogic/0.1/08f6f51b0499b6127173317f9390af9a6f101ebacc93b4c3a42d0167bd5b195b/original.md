```julia
struct DifferenceSigmoidMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Difference of two sigmoids. See also [`SigmoidMF`](@ref).

### Fields

  * `a1::Real`: slope of the first sigmoid.
  * `c1::Real`: center of the first sigmoid.
  * `a2::Real`: slope of the second sigmoid.
  * `c2::Real`: center of the second sigmoid.

### Example

```julia
mf = DifferenceSigmoidMF(5, 2, 5, 7)
```
