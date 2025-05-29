```
build_constraints_lmi!(m::JuMP.Model, A::SparseMatrixCSC{JuMP.AffExpr, Int}; verbose=false)
```

JuMPモデル`m`に制約`F_1 y_1 + F_2 y_2 + ... + F_n y_n + G ∈ PSDCone()`を追加します。
