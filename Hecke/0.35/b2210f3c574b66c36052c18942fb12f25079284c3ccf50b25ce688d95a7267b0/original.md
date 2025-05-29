```
direct_product(algebras::StructureConstantAlgebra...; task::Symbol = :sum)
  -> StructureConstantAlgebra, Vector{AbsAlgAssMor}, Vector{AbsAlgAssMor}
direct_product(algebras::Vector{StructureConstantAlgebra}; task::Symbol = :sum)
  -> StructureConstantAlgebra, Vector{AbsAlgAssMor}, Vector{AbsAlgAssMor}
```

Returns the algebra $A = A_1 \times \cdots \times A_k$. `task` can be ":sum", ":prod", ":both" or ":none" and determines which canonical maps are computed as well: ":sum" for the injections, ":prod" for the projections.
