```
hadi1994(multivariateData)
```

与えられた多変量データに対してHadi (1994)アルゴリズムを実行します。

# 引数

  * `multivariateData::AbstractMatrix{Float64}`: 多変量データ。

# 説明

アルゴリズムは初期のサブセットから始まり、ロバスト共分散行列と位置推定を得るためにサブセットを拡大します。このアルゴリズムは`hadi1992`の拡張です。

# 出力

  * `["outliers"]`: 外れ値のインデックスの配列
  * `["critical.chi.squared"]`: 外れ値を決定するための閾値
  * `["rth.robust.distance"]`: r番目のロバスト距離で、(r+1)番目のロバスト距離が閾値を超える最初のものです。

# 例

```julia-repl
julia> multidata = hcat(hbk.x1, hbk.x2, hbk.x3);

julia> hadi1994(multidata)
Dict{Any,Any} with 3 entries:
  "outliers"              => [2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
  "critical.chi.squared" => 7.81473
  "rth.robust.distance"   => 5.04541
```

# 参考文献 Hadi, Ali S. "A modification of a method for the dedection of outliers in multivariate samples" Journal of the Royal Statistical Society: Series B (Methodological) 56.2 (1994): 393-396.
