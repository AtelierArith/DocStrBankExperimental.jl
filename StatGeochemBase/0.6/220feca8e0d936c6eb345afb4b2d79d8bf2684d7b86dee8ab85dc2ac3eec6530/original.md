```julia
DictDataset(t::NamedTuple, elements=keys(t))
```

Convert a tuple-based dataset to a dict-based dataset. 

See also `TupleDataset`

### Examples

```julia
julia> t 
NamedTuple with 2 elements:
  La  = Vector{Float64}(100,)   [0.6809734028326375 ... 0.30665937715972313]
  Yb  = Vector{Float64}(100,)   [0.8851029525168138 ... 0.866246147690925]

julia> d = DictDataset(t)
Dict{String, Vector{Float64}} with 2 entries:
  "Yb" => [0.885103, 0.284384, 0.351527, 0.643542, 0.631274, 0.653966, 0.968414, 0.00204819, 0.0655173, 0.5343…
  "La" => [0.680973, 0.35098, 0.0198742, 0.139642, 0.0703337, 0.0328973, 0.639431, 0.245205, 0.424142, 0.48889…    
```
