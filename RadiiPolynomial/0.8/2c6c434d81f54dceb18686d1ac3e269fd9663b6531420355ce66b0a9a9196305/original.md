```
project!(C::LinearOperator, A::LinearOperator)
```

Represent `A` as a [`LinearOperator`](@ref) from `domain(C)` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project`](@ref).
