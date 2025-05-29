```
nest2ring!(m_ring_dst::HealpixMap{T, RingOrder, AAR},
           m_nest_src::HealpixMap{T, NestedOrder, AAN}) where {T, AAN, AAR}
```

ネストされた順序からリング順序にマップを変換します。このバージョンは、第二引数にネストされたマップを取り、第一引数に提供されたネストされたマップに書き込みます。これは標準的なJuliaの`func!(dst, src)`の規約に従います。

# 引数:

  * `m_ring_dst::HealpixMap{T, NestedOrder, AA}`: `NestedOrder`型のマップ
  * `m_nest_src::HealpixMap{T, NestedOrder, AAN}`: `RingOrder`型のマップ

# 戻り値:

  * `HealpixMap{T, RingOrder, AA}`: `RingOrder`に変換された入力マップ

# 例

```julia-repl
julia> m_nest = HealpixMap{Float64,NestedOrder}(rand(nside2npix(64)));

julia> m_ring = HealpixMap{Float64,RingOrder}(64);

julia> nest2ring!(m_ring, m_nest)
49152-element HealpixMap{Float64, RingOrder, Vector{Float64}}:
 0.33681791815569895
 ⋮
 0.9092457003948482
```
