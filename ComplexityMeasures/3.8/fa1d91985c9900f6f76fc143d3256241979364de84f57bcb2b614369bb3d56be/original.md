```
NaiveKernel(ϵ::Real; method = KDTree, w = 0, metric = Euclidean()) <: OutcomeSpace
```

An [`OutcomeSpace`](@ref) based on a "naive" kernel density estimation approach (KDE), as discussed in [PrichardTheiler1995](@citet).

Probabilities $P(\mathbf{x}, \epsilon)$ are assigned to every point $\mathbf{x}$ by counting how many other points occupy the space spanned by a hypersphere of radius `ϵ` around $\mathbf{x}$, according to:

$$
P_i( X, \epsilon) \approx \dfrac{1}{N} \sum_{s} B(||X_i - X_j|| < \epsilon),
$$

where $B$ gives 1 if the argument is `true`. Probabilities are then normalized.

## Keyword arguments

  * `method = KDTree`: the search structure supported by Neighborhood.jl. Specifically, use `KDTree` to use a tree-based neighbor search, or `BruteForce` for the direct distances between all points. KDTrees heavily outperform direct distances when the dimensionality of the data is much smaller than the data length.
  * `w = 0`: the Theiler window, which excludes indices $s$ that are within $|i - s| ≤ w$ from the given point $x_i$.
  * `metric = Euclidean()`: the distance metric.

## Outcome space

The outcome space `Ω` for `NaiveKernel` are the indices of the input data, `eachindex(x)`. Hence, input `x` is needed for a well-defined [`outcome_space`](@ref). The reason to not return the data points themselves is because duplicate data points may not get assigned same probabilities (due to having different neighbors).
