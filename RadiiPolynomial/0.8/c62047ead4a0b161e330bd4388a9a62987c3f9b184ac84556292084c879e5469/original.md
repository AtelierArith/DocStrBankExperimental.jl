```
project!(C::LinearOperator, ℐ::Integral)
```

Represent `ℐ` as a [`LinearOperator`](@ref) from `domain(C)` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project(::Integral, ::VectorSpace, ::VectorSpace)`](@ref) and [`Integral`](@ref)
