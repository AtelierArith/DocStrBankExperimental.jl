```
num_link_constraints(
    graph::OptiGraph,
    func_type::Type{<:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}}},
    set_type::Type{<:MOI.AbstractSet},
)
```

グラフ内の関数 `func_type` とセット `set_type` を持つリンク制約の総数を取得します。サブグラフ内の制約も含まれます。
