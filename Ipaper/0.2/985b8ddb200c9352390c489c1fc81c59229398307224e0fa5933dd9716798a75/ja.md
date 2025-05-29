```
movstd!(z::AbstractVector{FT}, x::AbstractVector{T}, win::Tuple{Int,Int}=(1, 1);
      skip_centre=false, ddof=1) where {FT<:Real, T<:Real}
```

入力ベクトル `x` の移動標準偏差を、`win` で定義されたウィンドウを使用して計算し、事前に割り当てられた出力ベクトル `z` に結果を格納します。

# 引数

  * `z`: 計算された標準偏差値を格納するための事前に割り当てられた出力ベクトル。
  * `x`: 実数の入力ベクトル。
  * `win`: ウィンドウサイズを指定するタプル `(win_left, win_right)`。デフォルトは `(1, 1)`。
  * `skip_centre`: `true` の場合、計算中に現在の要素がスキップされます。
  * `ddof`: 分散計算のための自由度のデルタ。分散は `(∑x² - ∑x*μ) / (N - ddof)` として計算されます。

# 戻り値

移動標準偏差を含む出力ベクトル `z`。ウィンドウ内の有効な値の数が `ddof` より大きくない場合、その位置には `NaN` が割り当てられます。

# 例

```julia
x = [1.0, 2.0, 3.0, 4.0, 5.0]
z = similar(x, Float64)
movstd!(z, x, (1, 1); skip_centre=false, ddof=1)
```
