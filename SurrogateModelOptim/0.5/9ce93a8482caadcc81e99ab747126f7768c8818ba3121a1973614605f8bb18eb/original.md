```
smoptimize(f::Function, search_range::Array{Tuple{Float64,Float64},1}; options=Options())
```

Optimize the function `f` in the range `search_range` using a Radial Basis Function based surrogate model.
