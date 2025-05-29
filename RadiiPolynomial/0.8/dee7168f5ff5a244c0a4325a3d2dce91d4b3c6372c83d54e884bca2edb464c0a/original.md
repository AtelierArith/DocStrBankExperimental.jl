```
project!(c::Sequence, A::LinearOperator{ParameterSpace,<:VectorSpace})
```

Represent `A` as a [`Sequence`](@ref) in `space(c)`. The result is stored in `c` by overwriting it.

See also: [`project`](@ref).
