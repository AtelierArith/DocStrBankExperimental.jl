```
pack(bsf::AbstractVector{Bool}) -> Tuple{String,Int}
```

バイナリベクトルを簡潔な表現にパックします。通常はログ出力用です。詳細は[`unpack`](@ref)を参照してください。

# 例

```jldoctest
julia> a = BitVector([1, 0, 1, 0, 1, 1]);  # XZY

julia> b = pack(a)  # (hex_value, length)
("2b", 6)
julia> unpack(b) == a
true
```
