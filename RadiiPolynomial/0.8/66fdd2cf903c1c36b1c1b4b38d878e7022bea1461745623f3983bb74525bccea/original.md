```
project(a::Sequence, ::ParameterSpace, codomain_dest::VectorSpace, ::Type{T}=eltype(a))
```

Represent `a` as a [`LinearOperator`](@ref) from `ParameterSpace` to `codomain_dest`.

See also: [`project!`](@ref).
