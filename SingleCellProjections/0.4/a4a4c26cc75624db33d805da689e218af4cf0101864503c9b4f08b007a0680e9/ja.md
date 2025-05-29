```
ttest!(data::DataMatrix, h1, [group_a], [group_b]; h0, kwargs...)
```

与えられた `h1`（対立仮説）と `h0`（帰無仮説）を用いてt検定を実行します。t検定の例には二群検定や線形回帰があります。

`ttest!` は `data.var` にt統計量、p値、および差の列を追加します。

使用例や計算およびパラメータの詳細については、[`ttest_table`](@ref)を参照してください。

さらに、`ttest!` は次の `kwarg` をサポートしています：

  * `prefix` - t統計量、p値、および差の出力列名はこの文字列で接頭辞が付けられます。指定がない場合は、`h1`、`group_a`、`group_b`、および `h0` から構築されます。

また、次も参照してください: [`ttest_table`](@ref)、[`ttest`](@ref)、[`ftest!`](@ref)、[`mannwhitney!`](@ref)
