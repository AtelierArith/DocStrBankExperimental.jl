```julia
checker_image()
checker_image(size)
checker_image(size, checkersCount)
checker_image(size, checkersCount, stripeWidth)

```

チェッカーボードパターンのファントムを生成する関数。この関数は、指定されたパラメータを使用してパターンでファントムのほとんどをカバーしようとする最善の努力アプローチを使用します。

# 引数

  * `size::Tuple{Integer, Integer}`: ファントムのサイズ
  * `checkersCount::Tuple{Integer, Integer}`: 各軸に沿って生成する正方形の数
  * `stripeWidth::Tuple{Integer, Integer}`: デフォルトは `(1, 1)`。正方形の間の線の幅を設定します

# 例

```jldoctest
julia> image = checker_image((8, 8), (2, 3), (2, 1))
8×8 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  1.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  1.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```
