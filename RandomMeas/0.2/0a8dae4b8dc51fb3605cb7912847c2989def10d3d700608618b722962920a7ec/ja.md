```
get_trace_moment(shadows::Array{<:AbstractShadow, 2}, kth_moment::Int; O::Union{Nothing, MPO}=nothing)
```

`AbstractShadow`オブジェクトの配列から単一のトレースモーメントを計算します。

# 引数

  * `shadows::Array{<:AbstractShadow, 2}`: 次元が`(n_ru, n_m)`のシャドウオブジェクトの配列で、`n_ru`はランダムユニタリの数、`n_m`は測定の数です。
  * `kth_moment::Int`: 計算するモーメント`k`（例：`k = 1, 2, ...`）。
  * `O::Union{Nothing, MPO}`（オプション）: 提供された場合、`Tr[O * ρ^k]`を計算します。そうでない場合、`Tr[ρ^k]`を計算します（デフォルト: `nothing`）。

# 戻り値

計算されたトレースモーメントをスカラーとして返します。

# 例

```julia
moment1 = get_trace_moment(shadows, 1)
moment2 = get_trace_moment(shadows, 2; O=my_operator)
```
