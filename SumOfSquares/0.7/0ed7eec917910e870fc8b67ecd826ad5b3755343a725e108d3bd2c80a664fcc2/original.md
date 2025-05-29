```
struct GramMatrix{T, B, U, MT <: AbstractMatrix{T}} <: AbstractGramMatrix{T, B, U}
    Q::MT
    basis::B
end
```

Gram matrix $x^\top Q x$ where `Q` is a symmetric matrix indexed by the vector of polynomials of the basis `basis`.
