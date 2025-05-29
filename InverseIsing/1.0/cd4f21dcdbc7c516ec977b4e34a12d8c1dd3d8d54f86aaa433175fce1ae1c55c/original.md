```
coef(gbm::GBM)
```

Get weight marix of a trained GBM.

# Examples

```jldoctest
julia> model = GBM(3)

julia> coef(model)
3×3 Array{Float64,2}:
 0.86902   0.4058     0.568231
 0.700701  0.0892165  0.399372
 0.224095  0.234413   0.380341
```
