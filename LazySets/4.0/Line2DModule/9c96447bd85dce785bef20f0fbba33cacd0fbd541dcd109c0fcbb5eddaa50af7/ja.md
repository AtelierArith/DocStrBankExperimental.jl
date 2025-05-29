# 拡張ヘルプ

```
intersection(L1::Line2D, L2::Line2D)
```

### 出力

三つの結果が可能です：

  * もし直線が同一であれば、結果は最初の直線です。
  * もし直線が平行であり、かつ同一でなければ、結果は空集合です。
  * それ以外の場合、結果は唯一の交点を持つ集合です。

### アルゴリズム

まず、直線が平行であるかどうかを確認します。そうでなければ、[クラメルの法則](https://en.wikipedia.org/wiki/Cramer%27s_rule)を使用して交点を計算します。

### 例

直線 $y = x$ が直線 $y = -x + 1$ と交差した場合、それぞれ自身と交差します：

```jldoctest
julia> intersection(Line2D([-1.0, 1], 0.0), Line2D([1.0, 1], 1.0))
Singleton{Float64, Vector{Float64}}([0.5, 0.5])

julia> intersection(Line2D([1.0, 1], 1.0), Line2D([1.0, 1], 1.0))
Line2D{Float64, Vector{Float64}}([1.0, 1.0], 1.0)
```
