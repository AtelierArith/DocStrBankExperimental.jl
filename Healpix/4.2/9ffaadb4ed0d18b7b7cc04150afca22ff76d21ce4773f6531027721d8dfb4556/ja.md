```
nest2ring(m_nest::HealpixMap{T, NestedOrder, AA}) where {T, AA}
```

ネストされた順序からリング順序にマップを変換します。このバージョンは、入力と同じ配列タイプの新しい配列を割り当てます。

# 引数:

  * `m_nest::HealpixMap{T, NestedOrder, AA}`: `NestedOrder`タイプのマップ

# 戻り値:

  * `HealpixMap{T, RingOrder, AA}`: `RingOrder`に変換された入力マップ

# 例

```julia-repl
julia> m_nest = HealpixMap{Float64,NestedOrder}(rand(nside2npix(64)));

julia> nest2ring(m_nest)
49152-element HealpixMap{Float64, RingOrder, Vector{Float64}}:
 0.4703834205807309
 ⋮
 0.3945848051663148
```
