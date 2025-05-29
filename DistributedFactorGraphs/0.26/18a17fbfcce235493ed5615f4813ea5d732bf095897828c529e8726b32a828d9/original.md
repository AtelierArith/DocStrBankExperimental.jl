```julia
getPPE(v)
getPPE(v, ppekey)

```

Get the parametric point estimate (PPE) for a variable in the factor graph for a given solve key.

Notes

  * Defaults on keywords `solveKey` and `method`

Related [`getPPEMean`](@ref), [`getPPEMax`](@ref), [`updatePPE!`](@ref), `mean(BeliefType)`
