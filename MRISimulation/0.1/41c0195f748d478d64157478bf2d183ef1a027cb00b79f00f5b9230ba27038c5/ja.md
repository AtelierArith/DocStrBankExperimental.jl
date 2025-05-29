```
epgRelaxation( R1::AbstractFloat, R2::AbstractFloat, t::AbstractFloat, F::Vector{T}, Z::Vector{T}) where T
```

は、EPG状態のセットにリラクゼーション行列を適用します。

# 引数

  * `R1::AbstractFloat`   - R1
  * `R2::AbstractFloat`   - R2
  * `t::AbstractFloat`    - 時間間隔の長さ（秒）
  * `F::Vector{T}`  - 横方向の位相ずれ統計
  * `Z::Vector{T}`  - 縦方向の位相ずれ統計
