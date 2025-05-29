```
delete_action(g, action, player_idx)
```

指定された `action` によって指定されたプレイヤーのアクションセットからアクションを削除した新しい `NormalFormGame` インスタンスを返します。

# 引数

  * `g::NormalFormGame` : `NormalFormGame` インスタンス。
  * `action::Union{PureAction, AbstractVector{<:PureAction}}` : 削除するアクション。
  * `player_idx::Integer` : アクションを削除するプレイヤーのインデックス。

# 戻り値

  * `::NormalFormGame` : 指定されたアクションが削除された `NormalFormGame` インスタンス。
