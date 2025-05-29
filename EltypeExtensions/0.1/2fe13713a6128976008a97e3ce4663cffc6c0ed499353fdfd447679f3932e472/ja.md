```
convert_precisiontype(T::Type, A, prec)
```

`A`を`T`の[`precisiontype`](@ref)に変換します。`prec`はオプションです。

  * `T`が静的精度を持つ場合（例：`Float64`）、`prec`は影響しません。
  * `T`が動的精度を持つ場合（例：`BigFloat`）、`prec`は変換の精度を指定します。`prec`が提供されない場合、精度は`T`からの外部設定によって決まります。
  * `T`が整数の場合、変換は`Rational`にも掘り下げます。対照的に、`Rational`全体は整数よりも「精度が高い」ため、[`precisiontype`](@ref)は`Rational`を展開しません。

# 例

```jldoctest; setup = :(using EltypeExtensions: convert_precisiontype)
julia> convert_precisiontype(BigFloat, 1//3+im, 128)
0.3333333333333333333333333333333333333338 + 1.0im

julia> convert_precisiontype(Float16, [[m/n for n in 1:3] for m in 1:3])
3-element Vector{Vector{Float16}}:
 [1.0, 0.5, 0.3333]
 [2.0, 1.0, 0.6665]
 [3.0, 1.5, 1.0]
```
