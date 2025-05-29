```
tobeginningofvariation!(g::Game)
```

Go to the beginning of the variation containing the current node of the game.

Steps back up the game tree until we reach the point where the first child node (i.e. the main line) is not contained in the current variation.
