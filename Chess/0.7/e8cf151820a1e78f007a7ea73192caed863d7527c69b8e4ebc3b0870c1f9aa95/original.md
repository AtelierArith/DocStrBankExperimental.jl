```
donullmove(b::Board)
```

Returns an identical board with the side to move switched.

The board `b` itself is left unchanged. A new board is returned that is identical in every way except that the side to move is the opposite. In other words, the function has the effect of "passing" and giving the other player the chance to move.

Note that this will result in an illegal position if the side to move at `b` is in check. It's the caller's responsibility to make sure `donullmove` is not used in that case.

There is a much faster destructive function `donullmove!` that should be called instead when high performance is required.
