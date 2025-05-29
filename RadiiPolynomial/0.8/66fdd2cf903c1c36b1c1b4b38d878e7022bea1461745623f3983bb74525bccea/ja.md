```
project(a::Sequence, ::ParameterSpace, codomain_dest::VectorSpace, ::Type{T}=eltype(a))
```

`a`を`ParameterSpace`から`codomain_dest`への[`LinearOperator`](@ref)として表現します。

参照: [`project!`](@ref).
