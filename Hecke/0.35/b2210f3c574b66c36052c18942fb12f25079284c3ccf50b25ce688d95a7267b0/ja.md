```
direct_product(algebras::StructureConstantAlgebra...; task::Symbol = :sum)
  -> StructureConstantAlgebra, Vector{AbsAlgAssMor}, Vector{AbsAlgAssMor}
direct_product(algebras::Vector{StructureConstantAlgebra}; task::Symbol = :sum)
  -> StructureConstantAlgebra, Vector{AbsAlgAssMor}, Vector{AbsAlgAssMor}
```

代数 $A = A_1 \times \cdots \times A_k$ を返します。`task` は ":sum", ":prod", ":both" または ":none" であり、計算される標準的な写像も決定します：":sum" は注入に対して、":prod" は射影に対して。
