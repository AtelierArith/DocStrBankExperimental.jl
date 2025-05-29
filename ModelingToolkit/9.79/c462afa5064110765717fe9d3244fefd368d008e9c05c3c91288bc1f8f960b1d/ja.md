```julia
variable_dependencies(sys::AbstractSystem; variables = unknowns(sys),
                      variablestoids = nothing)
```

各変数について、それを修正する方程式を特定し、[`BipartiteGraph`](@ref)として返します。

注意:

  * 依存関係は、変数インデックスをそれを修正する方程式のインデックスにマッピングする[`BipartiteGraph`](@ref)として返されます。
  * `variables`は、依存関係を特定するための変数のリストを示します。
  * `variablestoids`は、`Variable`を`variables`内のその`Int`インデックスにマッピングする`Dict`を示します。

例: [`equation_dependencies`](@ref)の例を続けると

```julia
variable_dependencies(jumpsys)
```
