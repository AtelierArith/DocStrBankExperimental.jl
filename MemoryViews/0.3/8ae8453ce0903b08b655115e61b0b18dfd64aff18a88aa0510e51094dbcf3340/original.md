```
split_last(v::MemoryView{T}) -> Tuple{T, MemoryView{T}}
```

Return the last element of `v` and all other elements as a new memory view.

This function will throw a `BoundsError` if `v` is empty.

See also: [`split_first`](@ref)

# Examples

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
