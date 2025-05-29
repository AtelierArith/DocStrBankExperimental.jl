```
Basis{T,N} <: AbstractBasis{T,N}

Basis(iter)
```

Construct a `Basis` whose elements are the elements of the `AbstractArray` or iterator `iter`. Internally, basis elements are stored in the given `AbstractArray` or otherwise in the `Array` obtained from `collect(iter)`.

See also [`AbstractBasis`](@ref), [`TensorBasis`](@ref).

# Examples

```jldoctest
julia> b = Basis(['a', 'b', 'x', 'y', 'z'])
Basis(['a', 'b', 'x', 'y', 'z'])

julia> length(b)
5

julia> i = toindex(b, 'x')
CartesianIndex(3,)

julia> b[i], b[3]
('x', 'x')

julia> length(Basis(Char[]))
0
```
