```
movmean(x::AbstractVector{T}, win::Tuple{Int, Int}=(1, 1); skip_centre=false) where {T<:Real}
```

1次元配列 `x` の単純移動平均を、`win` で定義されたウィンドウに基づいて計算し、`x` と同じサイズの配列を返します。

# 引数

  * `x::AbstractVector{T}`: 型 `T` の入力配列。
  * `win::Tuple{Int64, Int64}`: 各要素の左と右のウィンドウサイズを定義するタプル。デフォルトは `(1, 1)`。
  * `skip_centre::Bool`: `true` の場合、平均計算で中心要素がスキップされます。デフォルトは `false`。

# 戻り値

  * `Vector`: 移動平均を含む、`x` と同じサイズの配列。

# 例

```julia
x = [1, 2, 3, 4, 5]
win = (1, 1)
movmean(x, win)  # returns [1.5, 2.0, 3.0, 4.0, 4.5]
```
