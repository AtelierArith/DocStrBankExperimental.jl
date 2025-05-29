```
ContinuousEvolve(val::Union{Float64, Unitful.Quantity{Float64}}, var::Union{Float64, Unitful.Quantity{Float64}}, tree::BinaryTree)
```

Function to evolve a continuous trait along a BinaryTree, `tree` via Brownian motion. Takes in a starting value, `val` and a variance, `var`.
