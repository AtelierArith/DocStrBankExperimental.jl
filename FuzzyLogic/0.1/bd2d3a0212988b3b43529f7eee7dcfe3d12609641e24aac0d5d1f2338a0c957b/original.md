```julia
struct WeightedMF{MF<:FuzzyLogic.AbstractMembershipFunction, T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

A membership function scaled by a parameter $0 ≤ w ≤ 1$.

  * `mf::FuzzyLogic.AbstractMembershipFunction`: membership function.
  * `w::Real`: scaling factor.

### Example

```julia
mf = 0.5 * TriangularMF(1, 2, 3)
```
