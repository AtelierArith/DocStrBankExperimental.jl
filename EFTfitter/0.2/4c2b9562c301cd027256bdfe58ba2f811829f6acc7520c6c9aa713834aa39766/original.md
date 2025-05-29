```
struct EFTfitterModel
```

This is the central type for using EFTfitter. It comprises all information necessary for performing an analysis. Only active `Measurement` and `Correlation` objects will be considered.

Fields:  

  * `parameters::BAT.NamedTupleDist`
  * `measurements::NamedTuple{<:Any, <:Tuple{Vararg{Measurement}}}`
  * `BinnedMeasurements::NamedTuple{<:Any, <:Tuple{Vararg{BinnedMeasurement}}}`
  * `correlations::NamedTuple{<:Any, <:Tuple{Vararg{Correlation}}}`
  * `nuisances::Union{NamedTuple{<:Any, <:Tuple{Vararg{NuisanceCorrelation}}}, Nothing}`

Constructors:

```julia
EFTfitterModel(
    parameters::BAT.NamedTupleDist,
    measurements::NamedTuple{<:Any, <:Tuple{Vararg{AbstractMeasurement}}},
    correlations::NamedTuple{<:Any, <:Tuple{Vararg{AbstractCorrelation}}},
    nuisances::Union{NamedTuple{<:Any, <:Tuple{Vararg{NuisanceCorrelation}}}, Nothing} = nothing
)
```

Examples:

```julia
model = EFTfitterModel(parameters, measurements, correlations) # no nuisance correlations

model = EFTfitterModel(parameters, measurements, correlations, nuisances) # with nuisance correlations
)
```
