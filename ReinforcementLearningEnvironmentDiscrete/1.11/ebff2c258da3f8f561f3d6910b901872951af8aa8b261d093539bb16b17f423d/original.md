```
MDP(ns, na; init = "random")
MDP(; ns = 10, na = 4, init = "random")
```

Return MDP with `init in ("random", "uniform", "deterministic")`, where the keyword init determines how to construct the transition probabilites (see also  [`getprobvecrandom`](@ref), [`getprobvecuniform`](@ref), [`getprobvecdeterministic`](@ref)).
