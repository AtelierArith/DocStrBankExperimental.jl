```
recycle!(list::MoveList)
```

Recycle the move list in order to re-use for generating new moves.

This is useful when you want to avoid allocating too much heap memory. If you have a `MoveList` lying around that you no longer need, consider reusing it instead of creating a new one the next time you need to generate some moves.
