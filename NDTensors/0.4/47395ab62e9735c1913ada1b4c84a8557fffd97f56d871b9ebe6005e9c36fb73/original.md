```
random_unitary(n::Int,m::Int)::Matrix{ComplexF64}
random_unitary(::Type{ElT},n::Int,m::Int)::Matrix{ElT}
```

Return a random matrix U of dimensions (n,m) such that if n >= m, U'*U is the identity, or if m > n U*U' is the identity. Optionally can pass a numeric type as the first argument to obtain a matrix of that type.

Sampling is based on https://arxiv.org/abs/math-ph/0609050 such that in the case `n==m`, the unitary matrix will be sampled according to the Haar measure.
