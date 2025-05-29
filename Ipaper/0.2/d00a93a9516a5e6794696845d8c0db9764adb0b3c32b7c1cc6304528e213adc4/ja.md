```
weighted_movmean!(z::AbstractVector{FT}, x::AbstractVector{Tx}, w::AbstractVector{Tw}, 
    win::Tuple{Int,Int}=(1, 1); skip_centre=false) where {FT<:Real,Tx<:Real,Tw<:Real}
```

入力ベクトル `x` の加重移動平均を、`win` で定義されたウィンドウと指定された `weights` を使用して計算し、事前に割り当てられた出力ベクトル `z` に結果を格納します。

# 引数

  * `z`: 計算された加重移動平均値を格納するための事前に割り当てられた出力ベクトル。
  * `x`: 実数の入力ベクトル。
  * `w`: ウィンドウ内の要素に適用される重みのベクトル。`weights` の長さはウィンドウサイズ `(win_left + win_right + 1)` と等しくする必要があります。
  * `win`: ウィンドウサイズを指定するタプル `(win_left, win_right)`。デフォルトは `(1, 1)` です。
  * `skip_centre`: `true` の場合、計算中に現在の要素がスキップされます。

# 戻り値

加重移動平均値を含む出力ベクトル `z`。

# 例

```julia
x = [1.0, 2.0, 3.0, 4.0, 5.0]
w = [0.1, 0.8, 0.1]
z = similar(x, Float64)
weighted_movmean!(z, x, w, (1, 1); skip_centre=false)
```
