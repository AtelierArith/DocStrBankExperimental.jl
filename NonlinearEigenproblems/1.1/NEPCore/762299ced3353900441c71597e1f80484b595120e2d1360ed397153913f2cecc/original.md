```
abstract NEP
```

A `NEP` object represents a nonlinear eigenvalue problem. All NEPs should implement

```julia
size(nep::NEP,d)
```

and at least one of the following

  * M = [`compute_Mder(nep::NEP,λ::Number,i::Integer=0)`](@ref)
  * V = [`compute_Mlincomb(nep::NEP,λ::Number,V::AbstractVecOrMat,a::Vector)`](@ref) (or `compute_Mlincomb!`)
  * MM = [`compute_MM(nep::NEP,S,V)`](@ref)
