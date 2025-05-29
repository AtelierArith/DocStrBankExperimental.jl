```
add_semi_infinite_variable(model::JuMP.Model, var::SemiInfiniteVariable, 
                           key::Val{:ext_key_name})::GeneralVariableRef
```

最適化モデル `model` に半無限変数 `var` を追加し（`key` を使用）、正しい `InfiniteOpt` 変数参照を返します。これは、`write_model` が最適化モデルであるときに半無限変数を作成するために [`make_semi_infinite_variable_ref`](@ref) によって使用される内部メソッドです。これは、元の `InfiniteModel` を変更することなく、測定を拡張したい拡張機能にとって便利です。最適化モデルタイプに対してはエラーがスローされます。これが拡張される場合、半無限変数の参照を基盤となる [`SemiInfiniteVariable`](@ref) に向けるために、[`internal_semi_infinite_variable`](@ref) も拡張する必要があります。
