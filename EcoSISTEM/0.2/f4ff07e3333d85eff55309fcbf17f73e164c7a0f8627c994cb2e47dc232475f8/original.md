```
assign_traits!(tree::AbstractTree, start::Vector{Float64},
  σ²::Vector{Float64})
```

Function to evolve continuous functional traits through a phylogenetic tree through Brownian motion, with a starting value, `start`, and rate, `σ²`.
