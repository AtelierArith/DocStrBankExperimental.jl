```
GridBox(nGridPerEdge::Int, spacing, center=ntuple(_->eltype(spacing[begin])(0), 3); 
        canDiff::Bool=true, index::Int=0) -> 
GridBox{T, D}
```

立方体の `GridBox` を生成する方法。一般的な引数に加えて、`nGridPerEdge` は各次元のグリッドの数を指定します。グリッドボックスの次元は `center` の次元によって決まります。
