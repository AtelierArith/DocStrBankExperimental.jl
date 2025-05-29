```
get_history(r::Approximation)
```

有理近似の収束履歴を解析します。

# 引数

  * `r::Approximation`: 履歴を取得する近似

# 戻り値

  * `::Vector`: 近似の次数
  * `::Vector`: 近似の推定最大誤差
  * `::Vector{Vector}`: 近似の極
  * `::Vector{Vector}`: 近似の許可された極
  * `::Integer`: 最良の近似のインデックス

詳細は [`convergenceplot`](@ref) を参照してください。
