```
eval_dynamics(r::AbstractResourceSharer, u::AbstractVector, p, t)
```

Evaluates the dynamics of the resource sharer `r` at state `u`, parameters `p` and time `t`. Omitting `p` and `t` is allowed if the dynamics of `r` does not depend on them.
