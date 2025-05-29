```
get_objective(o::AbstractManifoldObjective, recursive=true)
```

デコレートされた `o` の（おそらく）デコレートされていない [`AbstractManifoldObjective`](@ref) を返します。デコレートされた目的が `o.objective` 内に目的を格納しており、[`dispatch_objective_decorator`](@ref) が `Val{true}` に設定されている限り、内部状態は自動的に抽出されます。

デコレートされた目的の中に格納されている目的は、デフォルトで `o.objective` にあると仮定されます。この動作を目的 `o` に対して変更するには、`_get_objective(o, ::Val{true}, recursive)` を上書きしてください。これは再帰的な場合と直接的な場合の両方に適用されます。

`recursive` が `false` に設定されている場合、すべてのデコレーターの代わりに最も外側のデコレーターのみが取り除かれます。
