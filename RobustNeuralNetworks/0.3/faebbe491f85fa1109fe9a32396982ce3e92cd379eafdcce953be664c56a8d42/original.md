```
direct_to_explicit(ps::AbstractRENParams{T}) where T
```

Convert direct parameterisation of LBDNs to explicit parameterisation.

Uses the parameterisation encoded in `ps` to construct an [`ExplicitLBDNParams`](@ref) object that naturally respects a user-defined Lipschitz bound.

# Arguments

  * `ps::AbstractLBDNParams`: Direct parameterisation of an LBDN to convert to an explicit parameterisation for model evaluation (eg: [`DenseLBDNParams`](@ref)).

See also [`DenseLBDNParams`](@ref).
