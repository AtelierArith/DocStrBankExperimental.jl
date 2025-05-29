```
mc!(mcres::M; 
  success_status::Vector{Symbol}=[:Success,:Terminated]
  kwargs...
) where M <: Union{MCResult, Vector{MCResult}, Vector{Pair}}
```

失敗したモンテカルロシミュレーションを単一の `Scenario` で再実行します。`MCResult` タイプを更新します。

例: `mc!(mcres)`

引数:

  * `mcres` : `MCResult` タイプのモンテカルロ結果
  * `success_status` : 成功ステータスのベクター。デフォルトは `[:Success,:Terminated]`
  * kwargs : `mc(scenario::Scenario, parameters_variation::Vector, num_iter::Int64)` でサポートされている他のソルバー関連の引数
