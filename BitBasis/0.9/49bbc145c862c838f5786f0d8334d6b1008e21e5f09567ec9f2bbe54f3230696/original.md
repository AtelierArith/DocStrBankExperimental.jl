```
onehot([T=Float64], dit_str[; nbatch])
```

Create an onehot vector in type `Vector{T}` or a batch of onehot vector in type `Matrix{T}`, where index `x + 1` is one. One can specify the value of the nonzero entry by inputing a pair.
