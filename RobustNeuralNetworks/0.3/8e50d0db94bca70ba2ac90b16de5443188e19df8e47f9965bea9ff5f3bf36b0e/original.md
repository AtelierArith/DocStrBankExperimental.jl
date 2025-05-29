```
direct_to_explicit(ps::AbstractRENParams{T}, return_h=false) where T
```

Convert direct parameterisation of RENs to explicit parameterisation.

Uses the parameterisation encoded in `ps` to construct an [`ExplicitRENParams`](@ref) object that naturally satisfies a set of user-defined behavioural constraints.

# Arguments

  * `ps::AbstractRENParams`: Direct parameterisation with behavioural constraints to convert to an explicit parameterisation of REN (eg: [`GeneralRENParams`](@ref)).
  * `return_h::Bool=false`: Whether to return the H-matrix directly (see [Revay et al. (2021)](https://arxiv.org/abs/2104.05942)). Useful for debugging or model analysis. If `false`, function returns an object of type `ExplicitRENParams{T}`.

See also [`GeneralRENParams`](@ref), [`ContractingRENParams`](@ref), [`LipschitzRENParams`](@ref), [`PassiveRENParams`](@ref).
