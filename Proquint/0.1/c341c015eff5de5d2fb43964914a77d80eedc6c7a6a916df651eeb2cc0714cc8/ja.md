```
uint2quint(x::T, sep="-"; short=false) where T<:Integer
```

整数値を対応するプロクイント文字列識別子に変換します。

# 引数

  * `x`: 整数引数、
  * `sep="-"`: セパレータ文字列、
  * `short=false`: 短い文字列を作成するかどうかを決定します。

# 例

```julia
julia> uint2quint(0x7f000001)
"lusab-babad"

julia> uint2quint(0x7f000001, short=true)
"lusab-d"
```
