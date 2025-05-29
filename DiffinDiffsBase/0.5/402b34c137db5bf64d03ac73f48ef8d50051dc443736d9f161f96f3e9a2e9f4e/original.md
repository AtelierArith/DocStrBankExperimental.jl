```
post!(f, ::StataPostHDF, r::AbstractDIDResult; kwargs...)
```

Export result `r` for Stata module [`posthdf`](https://github.com/junyuan-chen/posthdf). A subset of field values from `r` are placed in `f` by setting key-value pairs, where `f` can be either an `HDF5.Group` or any object that can be indexed by strings.

# Keywords

  * `model::String=repr(typeof(r))`: name of the model.
  * `fields::Union{AbstractVector{<:Union{Symbol, Pair{String,Symbol}}}, Nothing}=nothing`: additional fields to be exported; alternative names can be specified with `Pair`s.
  * `at::Union{AbstractVector{<:Real}, Bool, Nothing}=nothing`: post the `at` vector in Stata.
