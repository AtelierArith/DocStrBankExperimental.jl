```
delete_action(g, action, player_idx)
```

Return a new `NormalFormGame` instance with the action(s) specified by `action` deleted from the action set of the player specified by `player_idx`.

# Arguments

  * `g::NormalFormGame` : `NormalFormGame` instance.
  * `action::Union{PureAction, AbstractVector{<:PureAction}}` : The action(s) to be deleted.
  * `player_idx::Integer` : Index of the player to delete action(s) for.

# Returns

  * `::NormalFormGame` : `NormalFormGame` instance with the action(s) deleted as specified.
