```
Hex(v::AbstractVector{UInt8})
```

バイトベクターのラッパータイプ。このタイプがAuxiliaryに割り当てられると、これは生のバイト配列（タイプタグ `B`）ではなく、16進数値（タイプタグ `H`）としてエンコードされます。

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
