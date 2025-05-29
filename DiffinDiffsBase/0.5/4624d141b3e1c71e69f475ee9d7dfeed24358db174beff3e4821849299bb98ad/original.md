```
TreatmentTerm{T<:AbstractTreatment} <: AbstractTerm
```

A term that contains specifications on treatment and parallel trends assumption. See also [`treat`](@ref).

# Fields

  * `sym::Symbol`: the column name of data representing treatment status.
  * `tr::T`: a treatment type that specifies the causal parameters of interest.
  * `pr::P`: a parallel type that specifies the parallel trends assumption.
