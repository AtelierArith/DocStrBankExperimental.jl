```
MigrationPenalty(maxAct, λ, gridSize)
```

A concrete type that encourages cells to protude and drag themselves forward.

Two integer parameters control how cells protude:

  * `maxAct`: A maximum activity a grid location can have
  * `λ`: A parameter that controls the strength of this penalty
  * 'gridSize': The size of the space, simply supply size(space)

Increasing `maxAct` will cause grid locations to more likely protrude. Increasing `λ` will cause those protusions to reach farther away. 
