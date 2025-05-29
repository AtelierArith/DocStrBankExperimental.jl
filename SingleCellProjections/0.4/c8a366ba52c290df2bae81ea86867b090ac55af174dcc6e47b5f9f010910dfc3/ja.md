```
ftest(data::DataMatrix, h1; h0, var=:copy, obs=:copy, matrix=:keep, kwargs...)
```

与えられた `h1`（対立仮説）と `h0`（帰無仮説）を用いてF検定を実行します。F検定の例にはANOVAや二次回帰が含まれますが、任意の線形モデルを使用できます。

`ftest` は `data` のコピーを作成し、`data.var` にF統計量とp値の列を追加します。

使用例や計算およびパラメータの詳細については、[`ftest_table`](@ref) と [`ftest!`](@ref) を参照してください。

その他の情報: [`ftest!`](@ref), [`ftest_table`](@ref), [`ttest`](@ref)
