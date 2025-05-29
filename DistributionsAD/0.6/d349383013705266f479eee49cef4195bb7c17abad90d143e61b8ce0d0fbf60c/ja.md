```
filldist(d::Distribution, ns...)
```

単一の分布と次元サイズのリストから積分布を作成します。もし `size(d)` が `(d1, d2, ...)` で、`ns` が `(n1, n2, ...)` の場合、結果の分布はサイズ `(d1, d2, ..., n1, n2, ...)` になります。

デフォルトの動作は [`Distributions.product_distribution`](https://juliastats.org/Distributions.jl/stable/multivariate/#Distributions.product_distribution) を使用し、配列引数として `FillArrays.Fill` が提供されます。ただし、この動作は以下に示すようにいくつかのインスタンスで特化されています。

結果の分布からサンプリングすると、出力は元の分布 `d` からサンプリングされた各要素を持つ配列になります。

# 例

```jldoctest; setup=:(using Distributions, Random)
julia> d = filldist(Normal(0, 1), 4, 5);

julia> size(d)
(4, 5)

julia> rand(d) isa Matrix{Float64}
true
```
