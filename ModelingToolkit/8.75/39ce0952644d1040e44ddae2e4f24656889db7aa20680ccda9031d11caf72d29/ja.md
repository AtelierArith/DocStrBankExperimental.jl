```julia
asgraph(sys::AbstractSystem; variables = states(sys),
        variablestoids = Dict(convert(Variable, v) => i for (i, v) in enumerate(variables)))
```

`AbstractSystem`を[`BipartiteGraph`](@ref)に変換し、方程式のインデックスをそれらが依存する変数のインデックスにマッピングします。

ノート:

  * `equations(sys)`からそれらが依存する`states(sys)`へのマッピングを作成するためのkwargsのデフォルト。
  * `variables`は依存関係グラフを生成するために使用する変数のリストを提供する必要があります。
  * `variablestoids`は、`Variable`から`variables`内のその`Int`インデックスへの`Dict`のようなマッピングを提供する必要があります。

例: [`equation_dependencies`](@ref)で始まった例を続けると

```julia
digr = asgraph(jumpsys)
```
