```
LinFitness(coefs::AbstractVector{<:Real})
```

目的関数の出力 `y` の質を測定する線形フィットネス関数を定義するために使用されます。

一部の獲得関数は線形フィットネス関数で解析的に計算できるため、より一般的な `NonlinFitness` よりもパフォーマンスが向上する可能性がありますが、非線形フィットネス関数ではこれが不可能な場合があります。

関連情報: [`NonlinFitness`](@ref)

# 例

フィットネス関数 `f(y) = y[1] + a * y[2] + b * y[3]` は次のように定義できます：

```julia-repl
julia> LinFitness([1., a, b])
```
