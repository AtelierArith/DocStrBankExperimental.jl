```
precision(m::DBCM)
```

DBCMモデル`m`の計算精度を決定します。

# 例

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> MaxEntropyGraphs.precision(model)
Float64
```

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()), precision=Float32);

julia> MaxEntropyGraphs.precision(model)
Float32
```
