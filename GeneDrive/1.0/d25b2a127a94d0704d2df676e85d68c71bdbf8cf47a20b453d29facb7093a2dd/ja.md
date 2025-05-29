```
Release(node::Node, organism, stage::Type{T}, gene, times::Vector, variable_release::Vector{Float64}) where T <: LifeStage
```

生物的制御介入の詳細を指定する `Release` オブジェクトを返します。リリースサイズは時間とともに変動します。
