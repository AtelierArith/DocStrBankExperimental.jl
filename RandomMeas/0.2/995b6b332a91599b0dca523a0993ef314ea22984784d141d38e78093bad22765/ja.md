```
get_trace_moment(shadows::Vector{<:AbstractShadow}, kth_moment::Int; O::Union{Nothing, MPO}=nothing)
```

ラッパー関数。ベクトルを2D配列に再形成することによって、シャドウオブジェクトのベクトルに対して単一のトレースモーメントを計算します。

# 引数

  * `shadows::Vector{<:AbstractShadow}`: シャドウオブジェクトのベクトル。
  * `kth_moment::Int`: 計算するモーメントの順序 `k`。
  * `O::Union{Nothing, MPO}` (オプション): MPO可観測量。

# 戻り値

計算されたトレースモーメントをスカラーとして返します。

# 例

```julia
moment = get_trace_moment(shadows_vector, 2; O=my_operator)
```
