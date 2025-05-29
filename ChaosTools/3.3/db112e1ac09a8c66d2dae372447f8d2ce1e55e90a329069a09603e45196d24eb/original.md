```
lyapunov_from_data(R::StateSpaceSet, ks; kwargs...)
```

For the given dataset `R`, which is expected to represent a trajectory of a dynamical system, calculate and return `E(k)`, which is the average logarithmic distance between states of a neighborhood that are evolved in time for `k` steps (`k` must be integer). The slope of `E` vs `k` approximates the maximum Lyapunov exponent.

Typically `R` is the result of delay coordinates embedding of a timeseries (see DelayEmbeddings.jl).

## Keyword arguments

  * `refstates = 1:(length(R) - ks[end])`: Vector of indices that notes which states of the dataset should be used as "reference states", which means that the algorithm is applied for all state indices contained in `refstates`.
  * `w::Int = 1`: The [Theiler window](@ref).
  * `ntype = NeighborNumber(1)`: The neighborhood type. Either [`NeighborNumber`](@ref) or [`WithinRange`](@ref). See [Neighborhoods](@ref) for more info.
  * `distance = FirstElement()`: Specifies what kind of distance function is used in the logarithmic distance of nearby states. Allowed distances values are `FirstElement()` or `Euclidean()`, see below for more info. The metric for finding neighbors is always the Euclidean one.

## Description

If the dataset exhibits exponential divergence of nearby states, then it should hold

$$
E(k) \approx \lambda\cdot k \cdot \Delta t + E(0)
$$

for a *well defined region* in the $k$ axis, where $\lambda$ is the approximated maximum Lyapunov exponent. $\Delta t$ is the time between samples in the original timeseries. You can use [`linear_region`](@ref) with arguments `(ks .* Δt, E)` to identify the slope (= $\lambda$) immediately, assuming you have chosen sufficiently good `ks` such that the linear scaling region is bigger than the saturated region.

The algorithm used in this function is due to Parlitz[^Skokos2016], which itself expands upon Kantz[^Kantz1994]. In sort, for each reference state a neighborhood is evaluated. Then, for each point in this neighborhood, the logarithmic distance between reference state and neighborhood state(s) is calculated as the "time" index `k` increases. The average of the above over all neighborhood states over all reference states is the returned result.

If the `distance` is `Euclidean()` then use the Euclidean distance of the full `D`-dimensional points (distance $d_E$ in ref.[^Skokos2016]). If however the `distance` is `FirstElement()`, calculate the absolute distance of *only the first elements* of the points of `R` (distance $d_F$ in ref.[^Skokos2016], useful when `R` comes from delay embedding).

[^Skokos2016]: Skokos, C. H. *et al.*, *Chaos Detection and Predictability* - Chapter 1 (section 1.3.2), Lecture Notes in Physics **915**, Springer (2016)

[^Kantz1994]: Kantz, H., Phys. Lett. A **185**, pp 77–87 (1994)
