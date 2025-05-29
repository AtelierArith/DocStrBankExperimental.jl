```
delete_action(player, action[, player_idx=1])
```

指定された `action` によって、`player_idx` で指定されたプレイヤーのアクションセットからアクションを削除した新しい Player インスタンスを返します。

# 引数

  * `player::Player` : Player インスタンス。
  * `action::Union{PureAction,AbstractVector{<:PureAction}}`: 削除するアクション。
  * `player_idx::Integer` : アクションを削除するプレイヤーのインデックス。

# 戻り値

  * `::Player` : 指定されたアクションが削除された `Player` インスタンス。

# 例

```julia
julia> player = Player([3 0; 0 3; 1 1])
3×2 Player{2, Int64}:
 3  0
 0  3
 1  1

julia> delete_action(player, 3)
2×2 Player{2, Int64}:
 3  0
 0  3

julia> delete_action(player, 1, 2)
3×1 Player{2, Int64}:
 0
 3
 1
```
