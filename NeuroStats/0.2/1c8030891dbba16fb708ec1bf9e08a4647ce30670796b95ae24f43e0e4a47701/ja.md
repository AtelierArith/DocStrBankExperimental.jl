```
outlier_detect(x; <キーワード引数>)
```

外れ値を検出します。

# 引数

  * `x::AbstractVector`
  * `method::Symbol=iqr`: 検出方法:

      * `:iqr`: 四分位範囲
      * `:z`: zスコア
      * `:g`: グラブス検定

# 戻り値

  * `o::Vector{Bool}`: 外れ値のインデックス
