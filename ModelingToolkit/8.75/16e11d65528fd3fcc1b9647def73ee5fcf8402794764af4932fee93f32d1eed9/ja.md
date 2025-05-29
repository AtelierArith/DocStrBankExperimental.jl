```julia
asgraph(eqdeps, vtois)
```

方程依存関係のコレクションを、例えば `equation_dependencies` によって返されるものを [`BipartiteGraph`](@ref) に変換します。

ノート:

  * `vtois` は、`eqdeps` の各 `Variable` 依存関係からグラフで使用する変数の整数 idx への `Dict` のようなマッピングを提供する必要があります。

例: [`equation_dependencies`](@ref) で始まった例を続けると

```julia
digr = asgraph(equation_dependencies(jumpsys),
               Dict(s => i for (i, s) in enumerate(states(jumpsys))))
```
