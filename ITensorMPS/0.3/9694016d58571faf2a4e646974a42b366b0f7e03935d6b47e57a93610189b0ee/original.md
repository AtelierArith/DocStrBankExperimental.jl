```
sample(m::MPS)
```

Given a normalized MPS m with `orthocenter(m)==1`, returns a `Vector{Int}` of `length(m)` corresponding to one sample of the probability distribution defined by squaring the components of the tensor that the MPS represents
