```julia
classify(
    art::AdaptiveResonance.ARTModule,
    x::AbstractMatrix{T} where T<:Real;
    preprocessed,
    get_bmu
) -> Any

```

# Summary

Predict categories of 'x' using the ART model.

Returns predicted categories 'y_hat.'

# Arguments

  * `art::ARTModule`: ART or ARTMAP module to use for batch inference.
  * `x::RealMatrix`: the 2-D dataset containing columns of samples with rows of features.
  * `preprocessed::Bool=false`: flag, if the data has already been complement coded or not.
  * `get_bmu::Bool=false`, flag, if the model should return the best-matching-unit label in the case of total mismatch.

# Examples

```julia-repl
julia> my_DDVFA = DDVFA()
DDVFA
    opts: opts_DDVFA
    ...
julia> x, y = load_data()
julia> train!(my_DDVFA, x)
julia> y_hat = classify(my_DDVFA, y)
```

# Method List / Definition Locations

```julia
classify(art, x; preprocessed, get_bmu)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:554`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl).
