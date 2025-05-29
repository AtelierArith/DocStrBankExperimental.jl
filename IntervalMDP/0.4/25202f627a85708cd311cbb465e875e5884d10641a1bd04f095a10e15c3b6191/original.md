```
FiniteTimeSafety{VT <: Vector{<:CartesianIndex}, T <: Integer}
```

Finite time safety specified by a set of avoid states and a time horizon.  That is, denote a trace by $s_1 s_2 s_3 \cdots$, then if $A$ is the set of avoid states and $H$ is the time horizon, the property is 

$$
    \mathbb{P}(\forall k = \{0, \ldots, H\}, s_k \notin A).
$$
