```
ring2nest!(m_nest_dst::HealpixMap{T, NestedOrder, AAN},
           m_ring_src::HealpixMap{T, RingOrder, AAR}) where {T, AAR, AAN}
```

リング順序からネスト順序へのマップを変換します。このバージョンは、第二引数にネストマップを取り、第一引数に提供されたネストマップに書き込みます。標準のJulia `func!(dst, src)` 形式に従います。

# 引数:

  * `m_nest_dst::HealpixMap{T, NestedOrder, AAN}`: `RingOrder` 型のマップ
  * `m_ring_src::HealpixMap{T, RingOrder, AA}`: `RingOrder` 型のマップ

# 戻り値:

  * `HealpixMap{T, NestedOrder, AA}`: `NestedOrder` に変換された入力マップ

# 例

```julia-repl
julia> m_ring = HealpixMap{Float64,RingOrder}(rand(nside2npix(64)));

julia> m_nest = HealpixMap{Float64,RingOrder}(64);

julia> ring2nest!(m_nest, m_ring)
49152-element HealpixMap{Float64, NestedOrder, Vector{Float64}}:
 0.0673134062168923
 ⋮
 0.703460503535335
```
