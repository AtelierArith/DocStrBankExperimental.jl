```
project(A::LinearOperator, domain_dest::VectorSpace, codomain_dest::VectorSpace, ::Type{T}=eltype(A))
```

`A`を`domain_dest`から`codomain_dest`への[`LinearOperator`](@ref)として表現します。

参照: [`project!`](@ref).
