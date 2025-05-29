```
project!(C::LinearOperator, ℰ::Evaluation)
```

Represent `ℰ` as a [`LinearOperator`](@ref) from `domain` to `codomain`. The result is stored in `C` by overwriting it.

See also: [`project(::Evaluation, ::VectorSpace, ::VectorSpace)`](@ref) and [`Evaluation`](@ref).
