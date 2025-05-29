```
Signatures <: EnergyMap
```

An energy map based on signatures, a measure that uses the Earth Mover's Distance (EMD) to compute the discriminating measure of a coordinate. Signatures provide us with a fully data-driven representation, which can be efficiently used with EMD. This representation is more efficient than a histogram and is able to represent complex data structure with fewer samples.

Here, a signature for the coefficients in the $j$-th level, $k$-th node, $l$-th index of class $c$ is defined as

$s_{j,k,l}^{(c)} = \{(\alpha_{i;j,k,l}^{(c)}, w_{i;j,k,l}^{(c)})\}_{i=1}^{N_c}$

where $\alpha_{i;j,k,l}^{(c)}$ and $w_{i;j,k,l}^{(c)}$ are the expansion coefficients and weights at location $(j,k,l)$ for signal $i$ of class $c$ respectively. Currently, the two valid types of weights are `:equal` and `:pdf`.

# Parameters

  * `weight::Symbol`: (Default: `:equal`) Type of weight to be used to compute $w_{i;j,k,l}^{(c)}$. Available   methods are `:equal` and `:pdf`.

**See also:** [`EnergyMap`](@ref), [`TimeFrequency`](@ref), [`ProbabilityDensity`](@ref)
