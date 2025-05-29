```
project!(C::LinearOperator, Δ::Laplacian)
```

Represent `Δ` as a [`LinearOperator`](@ref) from `domain(C)` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project(::Laplacian, ::VectorSpace, ::VectorSpace)`](@ref) and [`Laplacian`](@ref)
