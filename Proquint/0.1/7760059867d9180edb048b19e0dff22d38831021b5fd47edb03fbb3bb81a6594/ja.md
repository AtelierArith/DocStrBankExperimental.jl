```
quint2uint(qs::String, U::Type{T}=UInt) where T<:Unsigned
```

プロクイント文字列識別子 `qs` を対応する整数値に変換します。

# 引数

  * `U`: 符号なし整数型 例: `UInt16`, `UInt32`, `UInt64` または `UInt128`

# 例

```julia
julia> quint2uint("lusab-babad", UInt32)
0x7f000001

julia> quint2uint("lusab-d", UInt32)
0x7f000001
```
