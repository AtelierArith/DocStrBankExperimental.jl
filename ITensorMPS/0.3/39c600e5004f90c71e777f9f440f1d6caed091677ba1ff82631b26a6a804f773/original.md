```
sample!(m::MPS)
```

Given a normalized MPS m, returns a `Vector{Int}` of `length(m)` corresponding to one sample of the probability distribution defined by squaring the components of the tensor that the MPS represents. If the MPS does not have an orthogonality center, orthogonalize!(m,1) will be called before computing the sample.
