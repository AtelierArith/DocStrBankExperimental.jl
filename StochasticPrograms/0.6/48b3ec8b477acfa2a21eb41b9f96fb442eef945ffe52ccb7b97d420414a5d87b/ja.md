```
has_values(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer; result::Int = 1)
```

`stage`のノードで、`scenario_index`のシナリオにおいて、結果インデックス`result`でクエリ可能なプライマルソリューションがソルバーに存在する場合は`true`を返し、そうでない場合は`false`を返します。
