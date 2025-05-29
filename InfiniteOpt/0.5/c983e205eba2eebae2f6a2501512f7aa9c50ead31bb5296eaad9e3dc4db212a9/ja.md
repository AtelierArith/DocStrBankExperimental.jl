```
JuMP.build_variable(_error::Function, ivref::GeneralVariableRef,
                    eval_supports::Dict{Int, Float64}; [check::Bool = true]
                    )::SemiInfiniteVariable{GeneralVariableRef}
```

`JuMP.build_variable` 関数を拡張して、無限変数/導関数/パラメータ関数 `ivref` に基づいて半無限変数を構築し、`eval_supports` による削減サポートを提供します。`check = true` の場合、入力が適切であることを確認します。`ivref` が無限変数でない場合、`eval_supports` が無限パラメータドメインに違反している場合、またはサポート次元が `ivref` の無限パラメータ次元と一致しない場合にエラーが発生します。これは、測定を評価するために使用される内部メソッドを意図しています。
