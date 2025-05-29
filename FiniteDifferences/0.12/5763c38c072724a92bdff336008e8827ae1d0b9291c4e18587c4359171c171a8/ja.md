```
backward_fdm(
    p::Int,
    q::Int;
    adapt::Int=1,
    condition::Real=DEFAULT_CONDITION,
    factor::Real=DEFAULT_FACTOR,
    max_range::Real=Inf,
    geom::Bool=false
)
```

`p`点の後方グリッドで有限差分法を構築します。

# 引数

  * `p::Int`: グリッドポイントの数。
  * `q::Int`: 推定する導関数の次数。

# キーワード

  * `adapt::Int=1`: 導関数の`p`次の大きさを推定するために別の有限差分法を使用します。これはステップサイズの計算に重要です。この手順を`adapt`回再帰します。
  * `condition::Real`: 条件数。[`DEFAULT_CONDITION`](@ref)を参照してください。
  * `factor::Real`: ファクター数。[`DEFAULT_FACTOR`](@ref)を参照してください。
  * `max_range::Real=Inf`: 導関数が推定される入力からの最大距離。
  * `geom::Bool`: 線形間隔のポイントの代わりに幾何学的に間隔を空けたポイントを使用します。

# 戻り値

  * `FiniteDifferenceMethod`: 指定された有限差分法。
