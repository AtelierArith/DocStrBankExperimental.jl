```
donullmove!(b::Board)
```

Destructively modify the board `b` by swapping the side to move.

The board is left unchanged except that the side to move is changed. In other words, the function has the effect of "passing" and giving the other player the chance to move.

Note that this will result in an illegal position if the side to move at `b` is in check. It's the caller's responsibility to make sure `donullmove` is not used in that case.

The function returns a value of type `UndoInfo`. You'll need this if you want to later call `undomove!()` to take back the move and get the original position back.
