```
tipping_probabilities(basins_before, basins_after) → P
```

Return the tipping probabilities of the computed basins before and after a change in the system parameters (or time forcing), according to the definition of [Kaszas2019](@cite).

The input `basins` are integer-valued arrays, where the integers enumerate the attractor, e.g. the output of [`basins_of_attraction`](@ref).

## Description

Let $\mathcal{B}_i(p)$ denote the basin of attraction of attractor $A_i$ at parameter(s) $p$. Kaszás et al [Kaszas2019](@cite) define the tipping probability from $A_i$ to $A_j$, given a parameter change in the system of $p_- \to p_+$, as

$$
P(A_i \to A_j | p_- \to p_+) =
\frac{|\mathcal{B}_j(p_+) \cap \mathcal{B}_i(p_-)|}{|\mathcal{B}_i(p_-)|}
$$

where $|\cdot|$ is simply the volume of the enclosed set. The value of $P(A_i \to A_j | p_- \to p_+)$ is `P[i, j]`. The equation describes something quite simple: what is the overlap of the basin of attraction of $A_i$ at $p_-$ with that of the attractor $A_j$ at $p_+$. If `basins_before, basins_after` contain values of `-1`, corresponding to trajectories that diverge, this is considered as the last attractor of the system in `P`.
