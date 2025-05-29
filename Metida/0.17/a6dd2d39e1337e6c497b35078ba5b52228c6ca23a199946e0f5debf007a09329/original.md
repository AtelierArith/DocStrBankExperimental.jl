```
LMM(model, data; contrasts=Dict{Symbol,Any}(),  random::Union{Nothing, VarEffect, Vector{VarEffect}} = nothing, repeated::Union{Nothing, VarEffect} = nothing, wts::Union{Nothing, AbstractVector, AbstractMatrix, AbstractString, Symbol} = nothing)
```

Make Linear-Mixed Model object.

`model`: is a fixed-effect model (`@formula`)

`data`: tabular data

`contrasts`: contrasts for fixed factors

`random`: vector of random effects or single random effect

`repeated`: is a repeated effect or vector

`wts`: regression weights (residuals).

Weigts can be set as `Symbol` or `String`, in this case weights taken from tabular data. If weights is vector then this vector applyed to R-side part of covariance matrix (see [Weights details](@ref weights_header)). If weights is matrix then R-side part of covariance matrix multiplied by corresponding part of weight-matrix.

See also: [`@lmmformula`](@ref)
