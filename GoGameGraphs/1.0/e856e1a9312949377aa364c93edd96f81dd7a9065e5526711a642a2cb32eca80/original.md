```
remap(source_board::Board, target_board::Board)
```

Compute a remapping of the vertices of the Game Graph generated from `source_board` to the Game Graph generated from `target_board`. `source_board` and `target_board` must be isomorphic.

```
remap(board::Board)
```

Like above where `target_board` is the `Board` with smallest id that is isomorphic to `source_board`.
