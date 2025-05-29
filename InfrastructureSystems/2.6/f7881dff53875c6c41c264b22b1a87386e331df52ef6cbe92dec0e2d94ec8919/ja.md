```
PiecewiseIncrementalCurve(initial_input::Union{Float64, Nothing}, x_coords::Vector{Float64}, slopes::Vector{Float64})
PiecewiseIncrementalCurve(input_at_zero::Union{Nothing, Float64}, initial_input::Union{Float64, Nothing}, x_coords::Vector{Float64}, slopes::Vector{Float64})
```

生産ポイント間の限界率（傾き）によって指定された分割線形曲線。非ゼロの初期値を持つ場合があります。

# 引数

  * `input_at_zero::Union{Nothing, Float64}`: （オプション、デフォルトは `nothing`）ゼロ生産時のコストで、曲線の一部を表しません
  * `initial_input::Union{Float64, Nothing}`: 最小生産ポイント `first(x_coords)` におけるコスト（ゼロ生産時ではなく）、曲線の開始を定義します
  * `x_coords::Vector{Float64}`: `n` 個の生産ポイントのベクトル
  * `slopes::Vector{Float64}`: ポイント間の曲線セグメントの `n-1` 個の限界率/傾きのベクトル
