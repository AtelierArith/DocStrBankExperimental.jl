```
basin_entropy(basins::Array{Integer}, ε = size(basins, 1)÷10) -> Sb, Sbb
```

Return the basin entropy [Daza2016](@cite) `Sb` and basin boundary entropy `Sbb` of the given `basins` of attraction by considering `ε`-sized boxes along each dimension.

## Description

First, the n-dimensional input `basins` is divided regularly into n-dimensional boxes of side `ε`. If `ε` is an integer, the same size is used for all dimensions, otherwise `ε` can be a tuple with the same size as the dimensions of `basins`. The size of the basins has to be divisible by `ε`.

Assuming that there are $N$ `ε`-boxes that cover the `basins`, the basin entropy is estimated as [Daza2016](@cite)

$$
S_b = \tfrac{1}{N}\sum_{i=1}^{N}\sum_{j=1}^{m_i}-p_{ij}\log(p_{ij})
$$

where $m_i$ is the number of unique IDs (integers of `basins`) in box $i$ and $p_{ij}$ is the relative frequency (probability) to obtain ID $j$ in the $i$ box (simply the count of IDs $j$ divided by the total in the box).

`Sbb` is the boundary basin entropy. This follows the same definition as $S_b$, but now averaged over only only boxes that contains at least two different basins, that is, for the boxes on the boundaries.

The basin entropy is a measure of the uncertainty on the initial conditions of the basins. It is maximum at the value `log(n_att)` being `n_att` the number of unique IDs in `basins`. In this case the boundary is intermingled: for a given initial condition we can find another initial condition that lead to another basin arbitrarily close. It provides also a simple criterion for fractality: if the boundary basin entropy `Sbb` is above `log(2)` then we have a fractal boundary. It doesn't mean that basins with values below cannot have a fractal boundary, for a more precise test see [`basins_fractal_test`](@ref). An important feature of the basin entropy is that it allows comparisons between different basins using the same box size `ε`.
