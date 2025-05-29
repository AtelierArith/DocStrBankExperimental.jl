```
project!(C::LinearOperator, J::UniformScaling)
```

Represent `J` as a [`LinearOperator`](@ref) from `domain(C)` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project`](@ref).
