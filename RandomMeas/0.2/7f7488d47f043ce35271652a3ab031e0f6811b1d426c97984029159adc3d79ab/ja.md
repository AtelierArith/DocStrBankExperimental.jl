```
get_trace_moments(shadows::Array{<:AbstractShadow, 2}, kth_moments::Vector{Int}; O::Union{Nothing, MPO}=nothing)
```

ラッパー関数。シャドウオブジェクトの配列から複数のトレースモーメントを計算します。

# 引数

  * `shadows::Array{<:AbstractShadow, 2}`: 次元が `(n_ru, n_m)` のシャドウオブジェクトの配列。
  * `kth_moments::Vector{Int}`: モーメントの次数のベクトル。
  * `O::Union{Nothing, MPO}` (オプション): MPOオブザーバブル; 提供された場合、各モーメントに対して `Tr[O * ρ^k]` を計算します（デフォルト: `nothing`）。

# 戻り値

`kth_moments` の各モーメントに対応するトレースモーメントのベクトル。

# 例

```julia
moments = get_trace_moments(shadows_array, [1, 2, 3])
```
