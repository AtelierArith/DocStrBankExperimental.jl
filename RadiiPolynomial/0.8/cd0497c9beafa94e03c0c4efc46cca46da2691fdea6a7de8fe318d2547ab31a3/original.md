```
project(a::Sequence, space_dest::VectorSpace, ::Type{T}=eltype(a))
```

Represent `a` as a [`Sequence`](@ref) in `space_dest`.

See also: [`project!`](@ref).
