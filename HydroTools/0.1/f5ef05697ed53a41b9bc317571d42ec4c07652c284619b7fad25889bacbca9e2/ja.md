```
HW_index(anorm::AbstractVector; p_left = 0.99)
HW_index(anorm::AbstractVector, dates; p_left=0.99)
```

与えられた異常ベクトル `anorm` の HW インデックスを計算します。

# 引数

  * `anorm::AbstractVector`: 異常スコアのベクトル。
  * `p_left::Float64=0.99`: 偽陽性の確率。

# 戻り値

以下のフィールドを持つ名前付きタプル：

  * `duration::Int`: 異常の持続時間。
  * `frequency::Int`: 異常イベントの数。
  * `intensity::Float64`: 最大異常スコア。
  * `volume::Float64`: 異常スコアの合計。
  * `PR::Float64`: 検出の確率。
  * `FAR::Float64`: 偽警報率。

# 例

```julia
julia> HW_index([0.1, 0.2, 0.3, 0.2, 0.1, 0, -0.1, 0.1, 0.2, 0.3])
(duration = 9, frequency = 2, intensity = 0.3, volume = 1.5, PR = 89.99999999999993, FAR = 0.9888888888888889)

julia> HW_index([-1, -1])
(duration = 0, frequency = 0, intensity = NaN, volume = NaN, PR = NaN, FAR = NaN)
```

# 参考文献

1. Kong, D., Gu, X., Li, J., Ren, G., & Liu, J. (2020). Contributions of Global Warming and Urbanization to the Intensification of Human‐Perceived Heatwaves Over China. Journal of Geophysical Research: Atmospheres, 125(18). [https://doi.org/10.1029/2019JD032175](https://doi.org/10.1029/2019JD032175)
