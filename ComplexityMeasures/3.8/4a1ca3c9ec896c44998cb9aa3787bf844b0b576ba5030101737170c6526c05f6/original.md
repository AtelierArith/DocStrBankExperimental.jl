```
Lord <: DifferentialInfoEstimator
Lord(measure = Shannon(); k = 10, w = 0)
```

The `Lord` estimator [Lord2018](@cite) estimates the [`Shannon`](@ref) differential [`information`](@ref) using a nearest neighbor approach with a local nonuniformity correction (LNC), with logarithms to the `base` specified in `definition`.

`w` is the Theiler window, which determines if temporal neighbors are excluded during neighbor searches (defaults to `0`, meaning that only the point itself is excluded when searching for neighbours).

## Description

Assume we have samples $\bar{X} = \{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$ from a continuous random variable $X \in \mathbb{R}^d$ with support $\mathcal{X}$ and density function $f : \mathbb{R}^d \to \mathbb{R}$. `Lord` estimates the [`Shannon`](@ref) differential entropy

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))],
$$

by using the resubstitution formula

$$
\hat{\bar{X}, k} = -\mathbb{E}[\log(f(X))]
\approx \sum_{i = 1}^N \log(\hat{f}(\bf{x}_i)),
$$

where $\hat{f}(\bf{x}_i)$ is an estimate of the density at $\bf{x}_i$ constructed in a manner such that $\hat{f}(\bf{x}_i) \propto \dfrac{k(x_i) / N}{V_i}$, where $k(x_i)$ is the number of points in the neighborhood of $\bf{x}_i$, and $V_i$ is the volume of that neighborhood.

While most nearest-neighbor based differential entropy estimators uses regular volume elements (e.g. hypercubes, hyperrectangles, hyperspheres) for approximating the local densities $\hat{f}(\bf{x}_i)$, the `Lord` estimator uses hyperellopsoid volume elements. These hyperellipsoids are, for each query point `xᵢ`, estimated using singular value decomposition (SVD) on the `k`-th nearest neighbors of `xᵢ`. Thus, the hyperellipsoids stretch/compress in response to the local geometry around each sample point. This makes `Lord` a well-suited entropy estimator for a wide range of systems.
