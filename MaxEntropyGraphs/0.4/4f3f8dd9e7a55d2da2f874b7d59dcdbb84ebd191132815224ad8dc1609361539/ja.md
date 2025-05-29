```
precision(m::UBCM)
```

UBCMモデル`m`の計算精度を決定します。

# 例

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> MaxEntropyGraphs.precision(model)
Float64
```

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate), precision=Float32);

julia> MaxEntropyGraphs.precision(model)
Float32
```
