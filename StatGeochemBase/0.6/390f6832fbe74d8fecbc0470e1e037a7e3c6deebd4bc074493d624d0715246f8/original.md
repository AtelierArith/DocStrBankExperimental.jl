```julia
TupleDataset(d::Dict, elements=keys(d))
```

Convert a dict-based dataset to a tuple-based dataset. 

See also `DictDataset`

### Examples

```julia
julia> d
Dict{String, Vector{Float64}} with 2 entries:
  "Yb" => [0.823733, 0.0531003, 0.47996, 0.560998, 0.001816, 0.455064, 0.694017, 0.737816, 0.0755015, 0.46098 …
  "La" => [0.440947, 0.937551, 0.464318, 0.694184, 0.253974, 0.521292, 0.857979, 0.0545946, 0.716639, 0.597616…

julia> t = TupleDataset(d)
NamedTuple with 2 elements:
  Yb  = Vector{Float64}(100,)   [0.8237334494155881 ... 0.012863893327602627]
  La  = Vector{Float64}(100,)   [0.44094669199955616 ... 0.5371416189174069]
```
