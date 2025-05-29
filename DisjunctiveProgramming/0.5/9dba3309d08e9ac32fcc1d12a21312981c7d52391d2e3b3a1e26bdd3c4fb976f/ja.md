```
requires_disaggregation(vref::JuMP.AbstractVariableRef)::Bool
```

`vref` が [`Hull`](@ref) 再定式化のために分解を必要とするかどうかを示す `Bool` を返します。これは、`JuMP.GenericVariableRef` ではない変数参照型を使用する DisjunctiveProgramming インターフェースの拡張ポイントとして意図されています。`vref` が `JuMP.GenericVariableRef` でない場合はエラーが発生します。詳細は [`make_disaggregated_variable`](@ref) を参照してください。
