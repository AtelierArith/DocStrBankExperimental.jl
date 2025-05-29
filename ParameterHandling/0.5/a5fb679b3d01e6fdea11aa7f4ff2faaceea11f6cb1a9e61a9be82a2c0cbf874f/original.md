```
positive(x::Array{<:Real})
```

Roughly equivalent to `map(positive, x)`, but implemented such that unflattening can be efficiently differentiated through using algorithmic differentiation (Zygote in particular).
