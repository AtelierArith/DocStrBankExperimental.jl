```
sample(treev::Array{T,1},
       f    ::Function,
       δt   ::Float64) where {T <: iTree}
```

Return an Array with a row for each sampled tree for interpolated parameters accessed by `f` at times determined by `δt`.
