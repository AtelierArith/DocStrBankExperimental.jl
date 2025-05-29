```
replace_ghost(indices,gids,owners)
```

Replaces the ghost indices in `indices` with global ids in `gids` and owners in   `owners`. Returned object takes ownership of `gids`  and `owners`. This method  only makes sense if `indices` stores ghost ids in separate vectors like in [`OwnAndGhostIndices`](@ref). `gids` should be unique and not being owned by  `indices`.
