```
project!(C::LinearOperator, 𝒮::Shift)
```

Represent `𝒮` as a [`LinearOperator`](@ref) from `domain(C)` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project(::Shift, ::VectorSpace, ::VectorSpace)`](@ref) and [`Shift`](@ref).
