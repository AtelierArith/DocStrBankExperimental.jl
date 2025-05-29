```
LBDN(ps::AbstractLBDNParams)
```

Construct an LBDN from its direct parameterisation.

This constructor takes a direct parameterisation of LBDN (eg: a [`DenseLBDNParams`](@ref) instance) and converts it to a **callable** explicit parameterisation of the LBDN. An example can be found in the docs for [`AbstractLBDN`](@ref).

See also [`AbstractLBDN`](@ref), [`DiffLBDN`](@ref).
