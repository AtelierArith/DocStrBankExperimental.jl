results(FastNet)        

*sim* の結果を DataFrame として返します

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[]);

julia> makenodes!(net,12,1)

julia> makenodes!(net,34,2)

julia> sim=FastSim(net,(r,t)->nothing,[])
シミュレーション実行中、現在の時間は 0.0

julia> runsim!(sim,100,25)
時間     ノード状態 1    ノード状態 2
  0.0              12              34
 25.0              12              34
 50.0              12              34
 75.0              12              34
100.0              12              34

julia> results(sim)
5×3 DataFrame
 Row │ 時間     ノード状態 1  ノード状態 2 
     │ Float64  Int64         Int64        
─────┼─────────────────────────────────────
   1 │     0.0            12            34
   2 │    25.0            12            34
   3 │    50.0            12            34
   4 │    75.0            12            34
   5 │   100.0            12            34 
```
