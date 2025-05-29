```
relative_eff(
    sample::AbstractArray{<:Real, 3};
    source::Union{AbstractString, Symbol} = "default",
    maxlag::Int = typemax(Int),
    kwargs..., 
)
```

Calculate the relative efficiency of an MCMC chain, i.e., the effective sample size divided by the nominal sample size.

If `lowercase(String(source))` is `"default"` or `"mcmc"`, the relative effective sample size is computed with `MCMCDiagnosticTools.ess`, using keyword arguments `kind = :basic`, `maxlag = maxlag`, and the remaining keyword arguments `kwargs...`. Otherwise a vector of ones for each chain is returned.

# Arguments

  * `sample::AbstractArray{<:Real, 3}`: An array of log-likelihood values of the shape `(parameters, draws, chains)`.
