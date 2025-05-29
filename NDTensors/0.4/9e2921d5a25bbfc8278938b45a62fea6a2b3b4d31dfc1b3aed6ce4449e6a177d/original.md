```
random_orthog(n::Int,m::Int)::Matrix{Float64}
random_orthog(::Type{ElT},n::Int,m::Int)::Matrix{ElT}
```

Return a random, real matrix O of dimensions (n,m) such that if n >= m, transpose(O)*O is the identity, or if m > n O*transpose(O) is the identity. Optionally can pass a real number type as the first argument to obtain a matrix of that type.
