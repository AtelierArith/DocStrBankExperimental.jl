```
SmallRationalGenerator()
SmallRationalGenerator(last_denominator)
```

(0,1] の範囲内で重複なしに有理数を生成するイテレータを作成します。

`last_denominator` が指定されている場合、その分母またはそれ以下の有理数のみを生成します（負の引数も同様の効果があります）。

例:

```
julia> collect(SmallRatGen(5))'
1×10 adjoint(::Vector{Rational{Int64}}) with eltype Rational{Int64}:
 1//1  1//2  1//3  2//3  1//4  3//4  1//5  2//5  3//5  4//5
```
