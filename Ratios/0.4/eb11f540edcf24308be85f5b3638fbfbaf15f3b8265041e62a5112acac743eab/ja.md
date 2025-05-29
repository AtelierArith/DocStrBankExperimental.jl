```
SimpleRatio(num::Integer, den::Integer)
```

`num // den`の有理数の同等物を構築します。

`SimpleRatio`を使用した演算は`Rational`よりも高速ですが、整数オーバーフローに対してもより脆弱です。`SimpleRatio`を使用した算術は、結果の比を簡略化しません。オーバーフローに対する最良の防御は、同じ分母を持つ比を使用することです。このような場合、`+`および`-`は分母の積を形成するのをスキップします。[`common_denominator`](@ref)を参照してください。

オーバーフローのリスクがある場合は、SaferIntegers.jlを使用して構築することを検討してください。

# 例

```julia
julia> x, y, z = SimpleRatio(1, 8), SimpleRatio(1, 4), SimpleRatio(2, 8)
(SimpleRatio{Int64}(1, 8), SimpleRatio{Int64}(1, 4), SimpleRatio{Int64}(2, 8))

julia> x+y
SimpleRatio{Int64}(12, 32)

julia> x+z
SimpleRatio{Int64}(3, 8)
```
