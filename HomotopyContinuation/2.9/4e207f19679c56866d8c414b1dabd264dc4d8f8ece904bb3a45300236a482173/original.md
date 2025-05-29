```
last_path_point(r::PathResult)
```

Returns a tuple `(x,t)` containing the last zero of `H(x, t)` before the Cauchy endgame was used. Returns `nothing` if the endgame strategy was not invoked.
