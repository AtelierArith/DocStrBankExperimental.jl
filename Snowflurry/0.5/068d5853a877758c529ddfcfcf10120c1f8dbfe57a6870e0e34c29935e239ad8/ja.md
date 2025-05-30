```
path_search(
    origin::Int,
    target::Int,
    connectivity::AbstractConnectivity,
    excluded::Vector{Int} = Vector{Int}([])
)::Vector{Int}
```

原点とターゲットのキュービット間の最短経路をマンハッタン距離に基づいて見つけます。この経路は、幅優先探索アルゴリズムを使用して、任意の `connectivity::AbstractConnectivity` に対して見つけられます。`excluded` オプション引数で指定された位置は回避されます。経路が存在しない場合は、空の `Vector{Int}` を返します。

# 例

```jldoctest
julia> connectivity = LineConnectivity(6)
LineConnectivity{6}
1──2──3──4──5──6


julia> path = path_search(2, 5, connectivity)
4-element Vector{Int64}:
 5
 4
 3
 2

```

[`LatticeConnectivity`](@ref) の場合、経路を視覚化するために [`print_connectivity()`](@ref) メソッドが使用されます。原点とターゲットの間の経路に沿ったキュービットは `( )` でマークされます。

```jldoctest; output=false
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


julia> path = path_search(3, 24, connectivity)
6-element Vector{Int64}:
 24
 20
 16
 12
  7
  3

```
