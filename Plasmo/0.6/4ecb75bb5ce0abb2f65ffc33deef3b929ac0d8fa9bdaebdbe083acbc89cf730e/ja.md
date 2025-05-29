```
num_local_link_constraints(
    graph::OptiGraph,
    func_type::Type{<:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}}},
    set_type::Type{<:MOI.AbstractSet},
)
```

グラフ内の関数 `func_type` とセット `set_type` に関連するローカルリンク制約の数を取得します。サブグラフ内のリンク制約は含まれません。
