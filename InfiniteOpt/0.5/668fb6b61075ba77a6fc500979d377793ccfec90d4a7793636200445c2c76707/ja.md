```
make_reduced_expr(vref::GeneralVariableRef, pref::GeneralVariableRef, 
                  support::Float64, write_model::Union{InfiniteModel, JuMP.Model})
```

引数変数 `vref` と演算子パラメータ `pref` を用いて、サポート `support` に従って `pref` に関する縮小式を構築し、返します。新しい点/半無限変数は `write_model` に書き込まれます。これは微分評価のための補助関数としてのみ意図されています。
