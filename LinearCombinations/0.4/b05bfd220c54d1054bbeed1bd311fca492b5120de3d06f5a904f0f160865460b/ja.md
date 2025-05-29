```
Basis{T,N} <: AbstractBasis{T,N}

Basis(iter)
```

`AbstractArray` またはイテレータ `iter` の要素からなる `Basis` を構築します。内部的には、基底要素は指定された `AbstractArray` に格納されるか、そうでなければ `collect(iter)` から得られた `Array` に格納されます。

[`AbstractBasis`](@ref) や [`TensorBasis`](@ref) も参照してください。

# 例

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
