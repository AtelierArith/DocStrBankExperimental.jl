```
ttest(data::DataMatrix, h1, [group_a], [group_b]; h0, var=:copy, obs=:copy, matrix=:keep, kwargs...)
```

与えられた `h1` (対立仮説) と `h0` (帰無仮説) を用いてt検定を実行します。t検定の例には二群検定や線形回帰があります。

`ttest` は `data` のコピーを作成し、t統計量、p値、および差の列を `data.var` に追加します。

使用例や計算およびパラメータの詳細については、[`ttest_table`](@ref) および [`ttest!`](@ref) を参照してください。

その他の参照: [`ttest!`](@ref), [`ttest_table`](@ref), [`ftest`](@ref), [`mannwhitney`](@ref)
