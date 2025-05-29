```
precision(m::BiCM)
```

BiCMモデル`m`の計算精度を決定します。

# 例

```jldoctest
julia> model = BiCM(corporateclub());

julia> MaxEntropyGraphs.precision(model)
Float64
```

```jldoctest
julia> model = BiCM(corporateclub(), precision=Float32);

julia> MaxEntropyGraphs.precision(model)
Float32
```
