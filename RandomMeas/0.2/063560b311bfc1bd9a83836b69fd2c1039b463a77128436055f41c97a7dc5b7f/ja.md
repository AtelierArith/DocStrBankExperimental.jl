```
get_trace_moments(shadows::Vector{<:AbstractShadow}, kth_moments::Vector{Int}; O::Union{Nothing, MPO}=nothing)
```

ラッパー関数。ベクトルを2D配列に再形成することによって、シャドウオブジェクトのベクトルから複数のトレースモーメントを計算します。

# 引数

  * `shadows::Vector{<:AbstractShadow}`: シャドウオブジェクトのベクトル。
  * `kth_moments::Vector{Int}`: モーメントの次数のベクトル。
  * `O::Union{Nothing, MPO}` (オプション): MPOオブザーバブル。

# 戻り値

トレースモーメントのベクトル。

# 例

```julia
moments = get_trace_moments(shadows_vector, [1, 2, 3])
```
