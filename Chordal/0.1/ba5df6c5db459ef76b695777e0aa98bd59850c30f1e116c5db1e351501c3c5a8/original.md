```
build_constraints_lmi!(m::JuMP.Model, A::SparseMatrixCSC{JuMP.AffExpr, Int}; verbose=false)
```

Adds the constraint `F_1 y_1 + F_2 y_2 + ... + F_n y_n + G ∈ PSDCone()` to JuMP model `m`
