```
build_constraints_lmi!(m::JuMP.Model, A::SparseMatrixCSC{JuMP.AffExpr, Int}; verbose=false)
```

制約 `A + S ∈ PSDCone()` を追加します。ここで `S ⪰ 0` は JuMP モデル `m` に対してです。
