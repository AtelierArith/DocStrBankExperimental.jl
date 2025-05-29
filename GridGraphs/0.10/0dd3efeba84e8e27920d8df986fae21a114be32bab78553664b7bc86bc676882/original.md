```
GridDirection
```

Enum type for the 9 possible move directions on a 2-dimensional grid with square cells: `northwest`, `west`, `southwest`, `north`, `center`, `south`, `northeast`, `east`, `southeast`.

Various subsets of these directions are defined as constants. They are based on an analogy with the game of chess:

  * `QUEEN_DIRECTIONS`
  * `ROOK_DIRECTIONS`
  * `QUEEN_DIRECTIONS_PLUS_CENTER`
  * `ROOK_DIRECTIONS_PLUS_CENTER`
  * `QUEEN_DIRECTIONS_ACYCLIC`
  * `ROOK_DIRECTIONS_ACYCLIC`

Acyclic direction sets give rise to an acyclic graph because they are contained in `{south, east, southeast}`.
