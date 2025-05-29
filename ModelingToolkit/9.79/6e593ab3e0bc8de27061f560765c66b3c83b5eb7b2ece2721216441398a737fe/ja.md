```julia
asgraph(eqdeps, vtois)
```

方程依存関係のコレクションを変換します。これは、`equation_dependencies`によって返されるものの例です。[`BipartiteGraph`](@ref)に変換されます。

ノート：

  * `vtois`は、`eqdeps`内の各`Variable`依存関係から、グラフで使用する変数の整数idxへの`Dict`のようなマッピングを提供する必要があります。

例：[`equation_dependencies`](@ref)で始まった例を続けます。

```julia
digr = asgraph(equation_dependencies(jumpsys),
               Dict(s => i for (i, s) in enumerate(unknowns(jumpsys))))
```
