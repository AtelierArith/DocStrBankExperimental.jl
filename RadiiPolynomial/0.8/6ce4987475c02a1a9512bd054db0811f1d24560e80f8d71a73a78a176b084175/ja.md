```
project(A::LinearOperator{ParameterSpace,<:VectorSpace}, space_dest::VectorSpace, ::Type{T}=eltype(A))
```

`A`を`space_dest`内の[`Sequence`](@ref)として表現します。

参照: [`project!`](@ref).
