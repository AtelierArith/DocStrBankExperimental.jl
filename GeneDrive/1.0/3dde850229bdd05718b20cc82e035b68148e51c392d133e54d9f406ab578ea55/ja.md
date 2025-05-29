```
ProportionalRelease(node::Node, organism, stage::Type{T}, gene_index, times::Vector, proportion::Float64, adult_counting::String) where T <: LifeStage
```

生物的制御介入の詳細を指定する `ProportionalRelease` オブジェクトを返します。リリースサイズはリアルタイムの野生個体群レベルに基づいています。
