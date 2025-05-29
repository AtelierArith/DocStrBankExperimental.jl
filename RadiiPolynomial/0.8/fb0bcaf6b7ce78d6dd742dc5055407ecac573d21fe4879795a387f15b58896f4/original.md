```
project!(C::LinearOperator, 𝒟::Derivative)
```

Represent `𝒟` as a [`LinearOperator`](@ref) from `domain(C)` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project(::Derivative, ::VectorSpace, ::VectorSpace)`](@ref) and [`Derivative`](@ref).
