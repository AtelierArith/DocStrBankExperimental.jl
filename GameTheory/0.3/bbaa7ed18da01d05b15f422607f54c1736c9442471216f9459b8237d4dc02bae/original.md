```
delete_action(player, action[, player_idx=1])
```

Return a new Player instance with the action(s) specified by `action` deleted from the action set of the player specified by `player_idx`.

# Arguments

  * `player::Player` : Player instance.
  * `action::Union{PureAction,AbstractVector{<:PureAction}}`: The action(s) to be deleted.
  * `player_idx::Integer` : Index of the player to delete action(s) for.

# Returns

  * `::Player` : `Player` instance with the action(s) deleted as specified.

# Examples

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
