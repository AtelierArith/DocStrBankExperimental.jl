```
connect_subgraphs_at_busses(net::Network{SinglePhase}, at_busses::Vector{String}, subgraphs::Vector{Vector})
```

splitting_bussesアルゴリズムは、サブグラフに重複を含めません。しかし、分解されたブランチフローモデルを解決するために、分割バスでの重複が必要です。したがって、ここでは各サブグラフに重複する分割バスを追加します。
