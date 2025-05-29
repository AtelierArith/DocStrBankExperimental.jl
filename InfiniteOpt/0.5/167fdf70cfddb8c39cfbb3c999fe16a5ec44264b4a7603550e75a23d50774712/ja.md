```
add_point_variable(model::JuMP.Model, ivref::GeneralVariableRef, 
                   support::Vector{Float64}, key::Val{:ext_key_name}
                   )::GeneralVariableRef
```

最適化モデル `model` にポイント変数（`ivref` を `support` に制限することによって定義される）を追加し、正しい `InfiniteOpt` 変数参照を返します。これは、`write_model` が最適化モデルであるときにポイント変数を作成するために [`make_point_variable_ref`](@ref) によって使用される内部メソッドです。これは、元の `InfiniteModel` を変更することなく、測定を拡張したい拡張機能にとって便利です。拡張されていない最適化モデルタイプに対してはエラーがスローされます。
