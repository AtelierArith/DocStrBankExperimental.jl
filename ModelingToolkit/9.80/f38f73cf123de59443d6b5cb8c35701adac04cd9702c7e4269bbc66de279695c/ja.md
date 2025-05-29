```julia
eqeq_dependencies(eqdeps::BipartiteGraph{T},
                  vardeps::BipartiteGraph{T}) where {T <: Integer}
```

各方程式が依存している方程式をマッピングする `LightGraph.SimpleDiGraph` を計算します。

ノート:

  * `SimpleDiGraph` の `fadjlist` は、方程式からその方程式が依存している変数を修正する方程式へのマッピングです。
  * `SimpleDiGraph` の `badjlist` は、方程式からその方程式が修正する変数に依存している方程式へのマッピングです。

例: `equation_dependencies` の例を続けると

```julia
eqeqdep = eqeq_dependencies(asgraph(jumpsys), variable_dependencies(jumpsys))
```
