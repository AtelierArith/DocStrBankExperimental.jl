```
post!(gl, gr, gd, ::StataPostHDF, cr::ContrastResult, left::Int=2, right::Int=3; kwargs...)
```

Export the least-square weights for coefficients indexed by `left` and `right` from `cr` for Stata module [`posthdf`](https://github.com/junyuan-chen/posthdf). The contribution of each cell to the difference between two coefficients are computed and also exported. The weights and contributions are stored as coefficient estimates in three groups `gl`, `gr` and `gd` respectively. The groups can be `HDF5.Group`s or objects that can be indexed by strings.

# Keywords

  * `lefttag::String=string(left)`: name to be used as `depvar` in Stata after being prefixed by `"l_"` for the coefficient indexed by `left`.
  * `righttag::String=string(right)`: name to be used as `depvar` in Stata after being prefixed by `"r_"` for the coefficient indexed by `right`.
  * `model::String="InteractionWeightedDIDs.ContrastResult"`: name of the model.
  * `eqnames::Union{AbstractVector, Nothing}=nothing`: equation names prefixed to coefficient names in Stata.
  * `colnames::Union{AbstractVector, Nothing}=nothing`: column names used as coefficient names in Stata.
  * `at::Union{AbstractVector{<:Real}, Nothing}=nothing`: the `at` vector in Stata.
