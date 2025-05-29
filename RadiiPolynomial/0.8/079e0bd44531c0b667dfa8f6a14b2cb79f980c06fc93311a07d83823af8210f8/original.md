```
project!(C::LinearOperator{<:SequenceSpace,<:SequenceSpace}, ℳ::Multiplication)
```

Represent `ℳ` as a [`LinearOperator`](@ref) from `domain(C)` to `codomain(C)`. The result is stored in `C` by overwriting it.

See also: [`project(::Multiplication, ::SequenceSpace, ::SequenceSpace)`](@ref) and [`Multiplication`](@ref).
