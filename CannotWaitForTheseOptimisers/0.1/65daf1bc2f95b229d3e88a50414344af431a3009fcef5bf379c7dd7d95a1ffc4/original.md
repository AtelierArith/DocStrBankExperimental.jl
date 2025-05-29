```
Apollo(opt::AdamW = AdamW(), r::Function = dim -> ceil(Int, sqrt(dim)); u = 100, sort_dims = true)
Apollo(η::Real, args...; kw...)
Apollo(arg, rank::Int; kw...)
Apollo(η::Real, rank::Int; kw...)
```

Apollo optimizer from Zhu et al. (https://arxiv.org/abs/2412.05270). Tracks moments in a low-rank subspace, aiming for Adam-like behavior with minimal additional memory usage. First argument can be an AdamW optimizer, or a learning rate (which will use the default AdamW optimizer with that learning rate). Second argument can be a rank, or a function to compute the rank from the second dimension (or the product of all dims > 1) of the weight matrix (or tensor).
