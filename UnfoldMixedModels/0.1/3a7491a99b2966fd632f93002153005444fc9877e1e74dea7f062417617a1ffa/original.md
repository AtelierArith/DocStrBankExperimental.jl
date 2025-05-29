```julia
pvalue(lrtvec)

```

Unfold-Method: return pvalues of likelihoodratiotests, typically calculated:

# Examples

julia> pvalue(likelihoodratiotest(m1,m2))

where m1/m2 are UnfoldLinearMixedModel's

Tipp: if you only compare two models you can easily get a vector of p-values:

julia> vcat(pvalues(likelihoodratiotest(m1,m2))...)

Multiple channels are returned linearized at the moment, as we do not have access to the amount of channels after the LRT, you can do:

julia> reshape(vcat(pvalues(likelihoodratiotest(m1,m2))...),ntimes,nchan)'
