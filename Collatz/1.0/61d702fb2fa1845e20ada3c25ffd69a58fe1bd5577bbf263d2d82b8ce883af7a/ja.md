```
tree_graph(initial_value, max_orbit_distance; P=2, a=3, b=1, __cycle_prevention=nothing)
```

最大ネストが max*orbit*distance までの有向木グラフをモデル化するネストされた辞書を返し、initial_value をルートとします。

# 引数

  * `initial_value::Integer`: 有向木グラフのルート値。
  * `max_orbit_distance::Integer`: 逆関数を繰り返す最大回数。木グラフを埋める自然な終了はなく、これは hailstone シーケンスや停止時間の試行の終了に相当するため、max*stopping*time / max*total*stopping_time のようなオプション引数ではなく、オービットを取得するための意図されたターゲットであり、無制限の計算を避けるための制限ではありません。

# キーワード引数

  * `P::Integer=2`: n を割るために使用されるモジュラス。n が (0 mod P) に相当する場合。
  * `a::Integer=3`: n を掛けるための係数。
  * `b::Integer=1`: n のスケール値に加える値。

# 内部キーワード引数

  * `__cycle_prevention::Union{Set{Integer},Nothing}=nothing`: 前のネスト深度で追加されたすべての値を追跡することでサイクルが発生するのを防ぐために使用されます。

# 例

```
julia> print(tree_graph(1, 3))
Dict{Int64, Dict{Any, Any}}(1 => Dict(2 => Dict{Any, Any}(4 => Dict{Any, Any}(Collatz._CC.CYCLE_INIT => 1, 8 => Dict{Any, Any}()))))
```

```
julia> print(tree_graph(4, 3))
Dict{Int64, Dict{Any, Any}}(4 => Dict(8 => Dict{Any, Any}(16 => Dict{Any, Any}(5 => Dict{Any, Any}(), 32 => Dict{Any, Any}())), 1 => Dict{Any, Any}(2 => Dict{Any, Any}(Collatz._CC.CYCLE_INIT => 4))))
```
