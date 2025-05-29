```julia
struct SingletonMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Singleton membership function. Equal to one at a single point and zero elsewhere.

### Fields

  * `c::Real`: Point at which the membership function has value 1.

### Example

```julia
mf = SingletonMF(4)
```
