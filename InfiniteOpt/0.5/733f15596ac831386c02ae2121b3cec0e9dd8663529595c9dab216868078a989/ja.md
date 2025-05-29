```
JuMP.add_variable(model::InfiniteModel, var::SemiInfiniteVariable,
                  [name::String = ""])::GeneralVariableRef
```

`JuMP.add_variable` 関数を拡張して `InfiniteOpt` 半無限変数タイプに対応します。`var` を無限モデル `model` に追加し、[`GeneralVariableRef`](@ref) を返します。主に測定を評価するために使用される内部関数を意図しています。
