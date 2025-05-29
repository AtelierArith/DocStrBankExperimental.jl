```
split_first(v::MemoryView{T}) -> Tuple{T, MemoryView{T}}
```

`v`の最初の要素と、残りのすべての要素を新しいメモリビューとして返します。

この関数は、`v`が空の場合に`BoundsError`をスローします。

参照: [`split_last`](@ref)

# 例

```jldoctest
julia> v = MemoryView([0x01, 0x02, 0x03]);

julia> split_first(v)
(0x01, UInt8[0x02, 0x03])

julia> split_first(v[1:1])
(0x01, UInt8[])

julia> split_first(v[1:0])
ERROR: BoundsError: attempt to access 0-element MutableMemoryView{UInt8} at index [1]
[...]
```
