```
unpack(packed_bsf::Tuple{String,Int}) -> BitVector
```

バイナリベクターを簡潔な表現から展開します。通常はログ出力からです。詳細は[`pack`](@ref)を参照してください。

# 例

```jldoctest
julia> a = ("2b", 6);  # (hex_value, length)

julia> b = unpack(a)  # XZY
6-element BitVector:
 1
 0
 1
 0
 1
 1
julia> pack(b) == a
true
```
