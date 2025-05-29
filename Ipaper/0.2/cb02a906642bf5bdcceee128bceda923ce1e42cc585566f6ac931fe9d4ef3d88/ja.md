```
movmean(x::AbstractVector{T}, win::Tuple{Int,Int}=(1, 1); skip_centre=false) where {T<:Real}
```

入力ベクトル `x` の移動平均を指定されたウィンドウサイズで計算します。

# 引数

  * `x::AbstractVector{T}`: 型 `T` の入力ベクトルで、`T` は `Real` のサブタイプです。
  * `win::Tuple{Int,Int}`: ウィンドウサイズ `(win_left, win_right)` を指定するタプル。デフォルトは `(1, 1)` です。
  * `skip_centre::Bool`: `true` の場合、平均計算で中心要素がスキップされます。デフォルトは `false` です。

# 戻り値

  * 入力ベクトル `x` と同じ長さの移動平均値を含むベクトル。

# 例

```julia
x = [1.0, 2.0, 3.0, 4.0, 5.0]
movmean(x, (1, 1))  # returns [1.5, 2.0, 3.0, 4.0, 4.5]
movmean(x, (1, 1); skip_centre=true)  # returns [1.0, 2.0, 3.0, 4.0, 5.0]
```
