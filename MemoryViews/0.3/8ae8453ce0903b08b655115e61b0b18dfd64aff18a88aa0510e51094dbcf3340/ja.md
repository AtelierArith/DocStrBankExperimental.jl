```
split_last(v::MemoryView{T}) -> Tuple{T, MemoryView{T}}
```

`v`の最後の要素と、他のすべての要素を新しいメモリビューとして返します。

この関数は、`v`が空の場合に`BoundsError`をスローします。

参照: [`split_first`](@ref)

# 例

```jldoctest
julia> v = MemoryView([0x01, 0x02, 0x03]);

julia> split_last(v)
(0x03, UInt8[0x01, 0x02])

julia> split_last(v[1:1])
(0x01, UInt8[])

julia> split_last(v[1:0])
ERROR: BoundsError: attempt to access 0-element MutableMemoryView{UInt8} at index [1]
[...]
```
