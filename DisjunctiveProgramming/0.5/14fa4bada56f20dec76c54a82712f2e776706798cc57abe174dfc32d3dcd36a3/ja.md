```
reformulate_disjunct_constraint(
    model::JuMP.AbstractModel,  
    con::JuMP.AbstractConstraint, 
    bvref::JuMP.AbstractVariableRef,
    method::AbstractReformulationMethod
)
```

制約 `con` の各制約に対して、再定式化メソッド `method` の拡張ポイントです。`method` が全体の選言をどのように再定式化するかを指定する必要がある場合は、[`reformulate_disjunction`](@ref) を参照してください。
