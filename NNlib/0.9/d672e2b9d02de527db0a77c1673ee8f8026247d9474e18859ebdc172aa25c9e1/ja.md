```
∇grid_sample(Δ::AbstractArray{T, 4}, input::AbstractArray{T, 4}, grid::AbstractArray{T, 4}; padding_mode = :zeros) where T
```

# 引数

  * `Δ`: 入力勾配の形状は `(W_out, H_out, C, N)` です（原始計算の出力と同じ）。
  * `input`: 原始計算からの入力の形状は `(W_in, H_in, C, N)` です。
  * `grid`: 原始計算からのグリッドの形状は `(2, W_out, H_out, N)` です。
  * `padding_mode`: 範囲外のパディング。範囲外のグリッド位置に `0` を使用するには `:zeros` を使用します。範囲外のグリッド位置に境界値を使用するには `:border` を使用します。原始計算と同じである必要があります。デフォルトは `:zeros` です。

# 戻り値

`dinput`（`input` と同じ形状）および `dgrid`（`grid` と同じ形状）の勾配。
