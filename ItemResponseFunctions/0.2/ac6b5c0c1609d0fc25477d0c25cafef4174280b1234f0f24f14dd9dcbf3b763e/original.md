```julia
struct ItemParameters{M<:AbstractItemResponseModels.ItemResponseModel, N, T<:Real}
```

A struct representing item parameters for an item response model.

## Fields

  * `a`: the item discrimination
  * `b`: the item difficulty (location)
  * `c`: the lower asymptote
  * `d`: the upper asymptote
  * `e`: the item stiffness
  * `t`: a tuple of threshold parameters

## Examples

```jldoctest
julia> pars = ItemParameters(TwoPL, a = 1.5, b = 0.0)
ItemParameters{TwoParameterLogisticModel, 0, Float64}(1.5, 0.0, 0.0, 1.0, 1.0, ())

julia> ItemParameters(OnePL, pars)
ItemParameters{OneParameterLogisticModel, 0, Float64}(1.0, 0.0, 0.0, 1.0, 1.0, ())
```
