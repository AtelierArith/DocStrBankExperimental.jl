```
expectation_value(ψ, O, [environments])
expectation_value(ψ, inds => O)
```

Compute the expectation value of an operator `O` on a state `ψ`.  Optionally, it is possible to make the computations more efficient by also passing in previously calculated `environments`.

In general, the operator `O` may consist of an arbitrary MPO `O <: AbstractMPO` that acts on all sites, or a local operator `O = inds => operator` acting on a subset of sites.  In the latter case, `inds` is a tuple of indices that specify the sites on which the operator acts, while the operator is either a `AbstractTensorMap` or a `FiniteMPO`.

# Arguments

  * `ψ::AbstractMPS` : the state on which to compute the expectation value
  * `O::Union{AbstractMPO,Pair}` : the operator to compute the expectation value of.    This can either be an `AbstractMPO`, or a pair of indices and local operator..
  * `environments::AbstractMPSEnvironments` : the environments to use for the calculation. If not given, they will be calculated.

# Examples

```jldoctest
julia> ψ = FiniteMPS(ones(Float64, (ℂ^2)^4));

julia> S_x = TensorMap(Float64[0 1; 1 0], ℂ^2, ℂ^2);

julia> round(expectation_value(ψ, 2 => S_x))
1.0

julia> round(expectation_value(ψ, (2, 3) => S_x ⊗ S_x))
1.0
```
