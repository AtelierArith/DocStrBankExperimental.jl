```
legal_action_space_mask(env, player=current_player(env)) -> AbstractArray{Bool}
```

[`FULL_ACTION_SET`](@ref) の環境に必要です。デフォルトの実装として、[`legal_action_space_mask`](@ref) は、サブセット [`legal_action_space`](@ref) を持つ [`action_space`](@ref) のマスクを作成します。
