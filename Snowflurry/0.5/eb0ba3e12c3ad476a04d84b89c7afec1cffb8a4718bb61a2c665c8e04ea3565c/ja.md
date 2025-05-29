```
get_qubits_distance(target_1::Int, target_2::Int, ::AbstractConnectivity)
```

ターゲットキュービット間の最短経路の長さをマンハッタン距離で求めます。この関数は、任意の `connectivity::AbstractConnectivity` の経路長を決定するために幅優先探索アルゴリズムを使用します。

# 例

```jldoctest
julia>  connectivity = LineConnectivity(6)
LineConnectivity{6}
1──2──3──4──5──6


julia> get_qubits_distance(2, 5, connectivity)
3

julia> connectivity = LatticeConnectivity(6, 4)
LatticeConnectivity{6,4}
              1 
              | 
        9 ──  5 ──  2 
        |     |     | 
 17 ── 13 ── 10 ──  6 ──  3 
  |     |     |     |     | 
 21 ── 18 ── 14 ── 11 ──  7 ──  4 
        |     |     |     |     | 
       22 ── 19 ── 15 ── 12 ──  8 
              |     |     | 
             23 ── 20 ── 16 
                    | 
                   24 


julia> get_qubits_distance(3, 24, connectivity)
5

```
