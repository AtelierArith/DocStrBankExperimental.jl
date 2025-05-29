```
Hex(v::AbstractVector{UInt8})
```

Wrapper type around a byte vector. When this type is assigned to an Auxiliary, it is encoded as a hex value (type tag `H`) as opposed to a raw byte array ( type tag `B`).

```jldoctest
julia> aux = SAM.Auxiliary(UInt8[], 1);

julia> aux["AB"] = Hex([0xae, 0xf8, 0x6c]);

julia> String(MemoryView(aux))
"AB:H:AEF86C"

julia> aux = BAM.Auxiliary(UInt8[], 1);

julia> aux["AB"] = Hex([0xae, 0xf8, 0x6c]);

julia> String(MemoryView(aux))
"ABHAEF86C\0"
```
