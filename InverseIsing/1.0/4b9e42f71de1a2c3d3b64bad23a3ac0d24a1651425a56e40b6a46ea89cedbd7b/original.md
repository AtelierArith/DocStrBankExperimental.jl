```
infer(gbm::GBM)
```

Infer GBM parameter matrix using trained weight.

# Examples

```jldoctest
julia> using InverseIsing

julia> model = GBM(3)

julia> infer(model)
3×3 Array{Int64,2}:
 1  1  1
 1  1  1
 1  1  1

julia> fit(model, [1 -1 -1;])

julia> infer(model)
3×3 Array{Int64,2}:
  0  -1  -1
 -1   0   1
 -1   1   0
```
