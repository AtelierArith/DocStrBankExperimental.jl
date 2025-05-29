```
JuMP.constraint_ref_with_index(backend::GraphMOIBackend, idx::MOI.Index)
```

グラフインデックスに関連付けられた制約参照（または変数参照）を `backend` から返します。`JuMP.ConstraintRef`（または `NodeVariableRef`）オブジェクトを返します。
