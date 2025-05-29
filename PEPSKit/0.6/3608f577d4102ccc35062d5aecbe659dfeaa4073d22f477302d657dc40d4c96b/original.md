```
struct SUWeight{E<:PEPSWeight}
```

Schmidt bond weights used in simple/cluster update. Weight elements are always real.

## Fields

  * `data::Array{E, 3} where E<:(TensorKit.AbstractTensorMap{T, S, 1, 1} where {T, S})`

## Constructors

```
SUWeight(wts_mats::AbstractMatrix{E}...) where {E<:PEPSWeight}
```
