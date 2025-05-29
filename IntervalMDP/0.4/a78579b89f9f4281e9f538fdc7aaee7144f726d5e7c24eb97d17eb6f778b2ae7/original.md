```
FiniteTimeReachAvoid{VT <: AbstractVector{<:CartesianIndex}}, T <: Integer}
```

Finite time reach-avoid specified by a set of target/terminal states, a set of avoid states, and a time horizon. That is, denote a trace by $s_1 s_2 s_3 \cdots$, then if $T$ is the set of target states, $A$ is the set of states to avoid, and $H$ is the time horizon, the property is 

$$
    \mathbb{P}(\exists k = \{0, \ldots, H\}, s_k \in T, \text{ and } \forall k' = \{0, \ldots, k\}, s_k' \notin A).
$$
