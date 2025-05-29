```
GridBox(nGridPerEdge::Int, spacing, center=ntuple(_->eltype(spacing[begin])(0), 3); 
        canDiff::Bool=true, index::Int=0) -> 
GridBox{T, D}
```

The method of generating a cubic `GridBox`. Aside from the common arguments, `nGridPerEdge`  specifies the number of grids for every dimension. The dimension of the grid box is  determined by the dimension of `center`.
