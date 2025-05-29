```
Tsallis <: InformationMeasure
Tsallis(q; k = 1.0, base = 2)
Tsallis(; q = 1.0, k = 1.0, base = 2)
```

The Tsallis generalized order-`q` entropy [Tsallis1988](@cite), used with [`information`](@ref) to compute an entropy.

`base` only applies in the limiting case `q == 1`, in which the Tsallis entropy reduces to [`Shannon`](@ref) entropy.

## Description

The Tsallis entropy is a generalization of the Boltzmann-Gibbs entropy, with `k` standing for the Boltzmann constant. It is defined as

$$
S_q(p) = \frac{k}{q - 1}\left(1 - \sum_{i} p[i]^q\right)
$$

The maximum value of the Tsallis entropy is $k(L^{1 - q} - 1)/(1 - q)$, with $L$ the [`total_outcomes`](@ref).
