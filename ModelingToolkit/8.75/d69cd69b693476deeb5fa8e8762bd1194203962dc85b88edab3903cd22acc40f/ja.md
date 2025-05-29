```julia
function varvar_dependencies(eqdeps::BipartiteGraph{T},
                             vardeps::BipartiteGraph{T}) where {T <: Integer}
    eqeq_dependencies(vardeps, eqdeps)
end
```

各変数が依存している変数にマッピングされる `LightGraph.SimpleDiGraph` を計算します。

ノート：

  * `SimpleDiGraph` の `fadjlist` は、変数からそれに依存している変数へのマッピングです。
  * `SimpleDiGraph` の `badjlist` は、変数からそれが依存している変数へのマッピングです。

例：`equation_dependencies` の例を続ける

```julia
varvardep = varvar_dependencies(asgraph(jumpsys), variable_dependencies(jumpsys))
```
