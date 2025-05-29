```
FiniteTimeReachability{VT <: Vector{<:CartesianIndex}, T <: Integer}
```

Finite time reachability specified by a set of target/terminal states and a time horizon.  That is, denote a trace by $s_1 s_2 s_3 \cdots$, then if $T$ is the set of target states and $H$ is the time horizon, the property is 

$$
    \mathbb{P}(\exists k = \{0, \ldots, H\}, s_k \in T).
$$
