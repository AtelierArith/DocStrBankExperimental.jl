```
pearson_match(p::Real, d1, d2; n::Real=12, m::Real=128, kwargs...)
```

ピアソン相関係数を計算し、二変量ガウスコピュラで使用します。

# フィールド

  * `p`: 周辺分布間の目標相関。
  * `d1`: 最初の周辺分布。
  * `d2`: 2番目の周辺分布。
  * `n`: 一致する相関を推定するために使用される多項式の次数。
  * `m`: エルミート多項式補間に使用される点の数。
  * `kwargs`: 追加のキーワード引数。現在は未使用。

# 例

```julia-repl
julia> using Distributions

julia> d1 = Beta(2, 3); d2 = Binomial(20, 0.2);

julia> pearson_match(0.6, d1, d2)
0.6127531346934495
```
