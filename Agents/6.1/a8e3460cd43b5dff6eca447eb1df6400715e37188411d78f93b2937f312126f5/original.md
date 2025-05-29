```
move_agent!(agent [, pos], model::ABM) → agent
```

Move agent to the given position, or to a random one if a position is not given. `pos` must have the appropriate position type depending on the space type.

The agent's position is updated to match `pos` after the move.
