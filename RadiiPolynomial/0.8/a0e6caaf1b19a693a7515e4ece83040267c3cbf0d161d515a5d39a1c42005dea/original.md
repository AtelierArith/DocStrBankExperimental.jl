```
project!(C::LinearOperator, 𝒮::Scale)
```

Represent `𝒮` as a [`LinearOperator`](@ref) from `domain(C)` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project(::Scale, ::VectorSpace, ::VectorSpace)`](@ref) and [`Scale`](@ref)
