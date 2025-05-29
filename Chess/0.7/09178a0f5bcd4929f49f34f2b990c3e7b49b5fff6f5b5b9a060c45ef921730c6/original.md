```
moves(b::Board, list::MoveList)
moves(b::Board)
```

Obtain a list of all legal moves from this board.

When performance is important, consider using the two-argument method that supplies a pre-allocated move list.
