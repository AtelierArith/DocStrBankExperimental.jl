```
build_constraints_lmi!(m::JuMP.Model, A::SparseMatrixCSC{JuMP.AffExpr, Int}; verbose=false)
```

Adds the constraint `A + S ∈ PSDCone()`, where `S ⪰ 0` to JuMP model `m`
