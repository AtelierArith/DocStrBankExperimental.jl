```julia
fuzzy_cmeans(
    X::Array{T<:Real, 2},
    N::Int64;
    m,
    maxiter,
    tol
) -> Tuple{Any, Any}

```

Performs fuzzy clustering on th data `X` using `N` clusters.

### Input

  * `X` – $d × M$ matrix of data, each column is a data point
  * `N` – number of clusters used.

### Keyword argumes

  * `m` – exponent of the fuzzy membership function, default `2.0`
  * `maxiter` – maximum number of iterations, default `100`
  * `tol` – absolute error for stopping condition. Stop if $|Eₖ - Eₖ₊₁|≤tol$, where $Eₖ$          is the cost function value at the $k$:th iteration.

### Output

  * `C` – $d × N$matrix of centers, each column is the center of a cluster.
  * `U` – $M × N$ matrix of membership degrees, `Uᵢⱼ``tells has the membership degree of        the``j``th point to the``i``th cluster.
