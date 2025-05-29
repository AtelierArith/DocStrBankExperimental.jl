```
clip_axes(sites::AtomList{D, T}, bounds::Vararg{Tuple{T,T},D}) where {D, T}
clip_axes(bounds...)
```

`bounds` で指定された D 次元タプルに基づいて、`bounds` の外にあるサイトを削除します。

```jldoctest; setup=:(using BloqadeLattices)
julia> sites = AtomList([(1.0, 2.0), (10.0, 3.0), (1.0, 12.0), (3.0, 5.0)])
4-element AtomList{2, Float64}:
 (1.0, 2.0)
 (10.0, 3.0)
 (1.0, 12.0)
 (3.0, 5.0)

julia> clip_axes(sites, (-5.0, 5.0), (-5.0, 5.0))
2-element AtomList{2, Float64}:
 (1.0, 2.0)
 (3.0, 5.0)
```
