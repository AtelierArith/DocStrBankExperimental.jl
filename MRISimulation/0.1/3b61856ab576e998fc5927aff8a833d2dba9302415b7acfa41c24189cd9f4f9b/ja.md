```
epgRotation(alpha::Float64, F::Vector{T}, Z::Vector{T}; statesConsidered=nothing, phi::Float64=0.0)
```

は、EPG状態のセットに対してBloch回転（<=> RFパルス）を適用します。

# 引数

  * `alpha::Float64`           - RFパルスのフリップ角
  * `F::Vector{T}`             - 横方向の脱相統計
  * `Z::Vector{T}`             - 縦方向の脱相統計
  * `statesConsidered=nothing` - 考慮する脱相状態の数（nothingはすべての状態が考慮されることを意味します）
  * `phi::Float64=0.0`         - RFパルスの位相
