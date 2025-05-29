```
hamilton_filter(y::AbstractVector, h::Integer, p::Integer; subset)
hamilton_filter(y::AbstractVector, freq::Symbol; subset)
```

`y`の時系列をHamilton（2018）による方法を使用して、循環成分とトレンド成分に分解します。

推定に無効な値（例：`NaN`、`Inf`、および`missing`）が含まれる`y`の行はスキップされます。返されるベクトルは`y`と同じ長さです。

# 引数

  * `y::AbstractVector`: フィルタリングされる時系列を格納するベクトル。
  * `h::Integer`: 予測のホライズン; ビジネスサイクルの場合、2年間をカバーする必要があります。
  * `p::Integer`: 推定に使用されるラグの数（現在のものを含む）。
  * `freq::Symbol`: データの頻度に基づいてHamilton（2018）が提案する`h`と`p`のデフォルト値を使用します; 月次、四半期、または年次データの場合は`:m`、`:q`、または`:y`である必要があります。

# キーワード

  * `subset::Union{BitVector,Nothing}=nothing`: フィルタリングされる`y`の行のブールインデックス。

# 返り値

  * `Vector{Float64}`: 循環成分。
  * `Vector{Float64}`: トレンド成分。
  * `BitVector`: 入力データ`y`の各行に対して推定が得られたかどうかの指標。

# 参考文献

Hamilton, James D. 2018. "Why You Should Never Use the Hodrick-Prescott Filter." The Review of Economics and Statistics 100 (5): 831-843.
