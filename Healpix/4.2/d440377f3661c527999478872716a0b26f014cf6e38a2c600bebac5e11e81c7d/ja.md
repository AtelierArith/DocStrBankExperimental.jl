```
ring2nest(m_ring::HealpixMap{T, RingOrder, AA}) where {T, AA}
```

リング順序からネスト順序にマップを変換します。このバージョンは、入力と同じ配列タイプの新しい配列を割り当てます。

# 引数:

  * `m_ring::HealpixMap{T, RingOrder, AA}`: `RingOrder`タイプのマップ

# 戻り値:

  * `HealpixMap{T, NestedOrder, AA}`: `NestedOrder`に変換された入力マップ

# 例

```julia-repl
julia> m_ring = HealpixMap{Float64,RingOrder}(rand(nside2npix(64)));

julia> ring2nest(m_ring)
49152-element HealpixMap{Float64, NestedOrder, Vector{Float64}}:
 0.0673134062168923
 ⋮
 0.703460503535335
```
