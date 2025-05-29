```
get_objective(o::AbstractManifoldObjective, recursive=true)
```

デコレートされた `o` の（1ステップの）デコレートされていない [`AbstractManifoldObjective`](@ref) を返します。デコレートされた目的が `o.objective` 内に目的を格納しており、[`dispatch_objective_decorator`](@ref) が `Val{true}` に設定されている限り、内部状態は自動的に抽出されます。

デコレートされた目的内に格納されている目的は、デフォルトで `o.objective` にあると仮定されます。この動作を、再帰的および直接の両方のケースで目的 `o` に対して変更するには、`_get_objective(o, ::Val{true}, recursive)` を上書きしてください。

`recursive` が `false` に設定されている場合、すべてではなく最も外側のデコレーターのみが取り除かれます。
