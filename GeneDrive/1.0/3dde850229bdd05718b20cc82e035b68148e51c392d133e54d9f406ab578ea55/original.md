```
ProportionalRelease(node::Node, organism, stage::Type{T}, gene_index, times::Vector, proportion::Float64, adult_counting::String) where T <: LifeStage
```

Return `ProportionalRelease` object specifying details of biological control intervention where release size is predicated on real-time wild population level.
