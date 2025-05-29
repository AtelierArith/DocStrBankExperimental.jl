```julia
struct Type2MF{MF1<:FuzzyLogic.AbstractMembershipFunction, MF2<:FuzzyLogic.AbstractMembershipFunction} <: FuzzyLogic.AbstractMembershipFunction
```

A type-2 membership function.

  * `lo::FuzzyLogic.AbstractMembershipFunction`: lower membership function.
  * `hi::FuzzyLogic.AbstractMembershipFunction`: upper membership function.

### Example

```julia
mf = 0.7 * TriangularMF(3, 5, 7) .. TriangularMF(1, 5, 9)
```
