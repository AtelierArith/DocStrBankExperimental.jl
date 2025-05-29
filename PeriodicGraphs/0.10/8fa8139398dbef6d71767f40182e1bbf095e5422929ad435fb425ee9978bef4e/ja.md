```
truncated_graph(g::PeriodicGraph)
```

`g`から初期セル内に厳密に存在するエッジのみを保持することで、単純グラフを抽出します。

すべてのエッジを保持するには[`quotient_graph`](@ref)を、これらのエッジの一部のみを保持するには[`slice_graph`](@ref)を参照してください。
