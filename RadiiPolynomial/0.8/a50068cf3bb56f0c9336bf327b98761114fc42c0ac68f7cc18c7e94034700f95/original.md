```
project!(C::LinearOperator{ParameterSpace,<:VectorSpace}, a::Sequence)
```

Represent `a` as a [`LinearOperator`](@ref) from `ParameterSpace` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project`](@ref).
