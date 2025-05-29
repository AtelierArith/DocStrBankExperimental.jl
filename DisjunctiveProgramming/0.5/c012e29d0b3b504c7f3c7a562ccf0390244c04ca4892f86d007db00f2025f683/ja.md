```
make_disaggregated_variable(
    model::JuMP.AbstractModel, 
    vref::JuMP.AbstractVariableRef, 
    name::String, 
    lower_bound::Number, 
    upper_bound::Number
    )::JuMP.AbstractVariableRef
```

`model`に名前`name`と境界`lower_bound`および`upper_bound`を持つ変数を作成して追加します。これは、元の変数`vref`に基づいています。これは、[`Hull`](@ref) 再定式化に必要な分解変数を作成するために使用されます。これは`model::JuMP.GenericModel`および`vref::JuMP.GenericVariableRef`に対して実装されていますが、他のモデル/変数参照タイプとのインターフェースの拡張ポイントとして機能します。これには、[`requires_disaggregation`](@ref) の実装も必要です。
