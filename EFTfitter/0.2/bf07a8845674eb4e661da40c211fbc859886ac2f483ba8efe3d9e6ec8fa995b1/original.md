```
struct BinnedMeasurement
```

Fields:       * `observable::Array{Observable, 1}`: Observables that are measured.     * `values::Array{Float64, 1}`: Measured values.     * `uncertainties::NamedTuple{<:Any, <:Tuple{Vararg{Array{Float64, 1}}}}`: Uncertainties of the measurement as NamedTuple.     * `active::Array{Bool, 1}`: Use or exclude bins in fit. Defaults to `true` for all bins.     * `bin_names::Array{Symbol, 1}`: Suffixes that will be appended to the name of the measurement distribution for the individual bins. Defaults to [_bin1, _bin2, ...].

Constructors:  

```julia
BinnedMeasurement(
    observable::Array{Observable, 1},
    values::Array{<:Real, 1};
    uncertainties::NamedTuple{<:Any, <:Tuple{Vararg{Union{Vector{Float64}, Vector{Int64}}}}},
    active::Union{Bool, Array{Bool, 1}} = [true for i in 1:length(vals)],
    bin_names::Array{Symbol, 1} = [Symbol("bin$i") for i in 1:length(vals)]
)
```

```julia
BinnedMeasurement(
    observable::Array{Function, 1},
    values::Array{<:Real, 1};
    uncertainties::NamedTuple{<:Any, <:Tuple{Vararg{Union{Vector{Float64}, Vector{Int64}}}}},
    active::Union{Bool, Array{Bool, 1}} = [true for i in 1:length(vals)],
    bin_names::Array{Symbol, 1}
)
```
