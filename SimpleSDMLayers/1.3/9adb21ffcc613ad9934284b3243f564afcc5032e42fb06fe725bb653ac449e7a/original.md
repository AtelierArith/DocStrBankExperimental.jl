```
burnin(L::SDMLayer, v::Vector{T}) where {T}
```

Writes the value of `v` in a layer similar to `L`, and returns it. It is ASSUMED (but essentially impossible to check) that the values of `v` are presented in the correct order. This uses `burnin!` internally.
