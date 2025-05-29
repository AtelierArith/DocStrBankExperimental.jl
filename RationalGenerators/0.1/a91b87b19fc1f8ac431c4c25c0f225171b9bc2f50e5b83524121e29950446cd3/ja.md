```
RationalGenerator(n)
RationalGenerator()
```

重複なしで正の有理数を生成するイテレータを作成します。

  * `RationalGenerator(n)` は、`gcd(a,b) = 1` かつ `a+b ≤ n` を満たす形のすべての有理数 `a//b` を生成します。
  * `RationalGenerator()` は、すべての有理数を生成します。負の引数で `RationalGenerator` を呼び出すことは同じ効果があります。

注意: `RatGen` は `RationalGenerator` の省略形として使用できます。

例:

```
julia> collect(RatGen(5))'
1×9 adjoint(::Vector{Rational{Int64}}) with eltype Rational{Int64}:
 1//1  1//2  2//1  1//3  3//1  1//4  2//3  3//2  4//1
```
