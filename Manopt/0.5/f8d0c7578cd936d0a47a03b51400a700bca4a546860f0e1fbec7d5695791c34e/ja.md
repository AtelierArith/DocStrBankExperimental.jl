```
get_state(s::AbstractManoptSolverState, recursive::Bool=true)
```

デコレートされた `s` の（おそらく）デコレートされていない [`AbstractManoptSolverState`](@ref) を返します。デコレートされた状態が `s.state` 内に状態を保存しており、[`dispatch_objective_decorator`](@ref) が `Val{true}` に設定されている限り、内部状態は自動的に抽出されます。

デコレートされた状態内に保存される状態は、デフォルトで `s.state` にあると仮定されます。この動作を変更するには、両方の再帰的および直接的なケースのために `_get_state(s, ::Val{true}, recursive)` を上書きしてください。

`recursive` が `false` に設定されている場合、すべてではなく最も外側のデコレーターのみが取り除かれます。
