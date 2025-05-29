```
RateCurve(reference_date::Real, tenors::AbstractVector, dfs::AbstractVector; interp = ...)
```

割引率とテナーから `RateCurve` を構築します。

# 引数

  * `reference_date`: 内部ティック単位での時間参照。
  * `tenors`: 年の分数のベクター（ソートされていて空であってはいけません）。
  * `dfs`: 各テナーに対応する割引率。
  * `interp`: ゼロ金利とテナーを補間オブジェクトにマッピングするビルダ関数 `(u, t) -> interpolator`。

# 戻り値

  * `RateCurve` インスタンス。
