```
project(A::LinearOperator{ParameterSpace,<:VectorSpace}, space_dest::VectorSpace, ::Type{T}=eltype(A))
```

Represent `A` as a [`Sequence`](@ref) in `space_dest`.

See also: [`project!`](@ref).
