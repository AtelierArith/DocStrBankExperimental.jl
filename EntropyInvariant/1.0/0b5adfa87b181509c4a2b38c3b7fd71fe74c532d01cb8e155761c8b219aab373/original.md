```
conditional_mutual_information(X::Matrix{<:Real}, Y::Union{Matrix{<:Real}, Nothing} = nothing, Z::Union{Matrix{<:Real}, Nothing} = nothing; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1, optimize::Bool = false) -> Real
```

Compute the conditional mutual information (CMI) between two datasets given a third conditioning dataset as   I(X; Y | Z) = H(X, Z) + H(Y, Z) - H(X, Y, Z) - H(Z), where:

  * H(Z): Entropy of the conditioning dataset Z.
  * H(X, Z): Joint entropy of X and Z.
  * H(Y, Z): Joint entropy of Y and Z.
  * H(X, Y, Z): Joint entropy of X, y and Z.

# Arguments

  * X::Vector or Matrix{<:Real}`: A matrix where each column represents a data point and each row represents a dimension for the first dataset.
  * Y::Vector or Matrix{<:Real}`: A matrix where each column represents a data point and each row represents a dimension for the second dataset.
  * Z::Vector or Matrix{<:Real}`: A matrix where each column represents a data point and each row represents a dimension for the conditioning dataset.
  * `method::String = "inv"` (optional): The method to use for entropy computation. Options are:

      * `"knn"`: k-Nearest Neighbors based entropy estimation.
      * `"histogram"`: Histogram-based entropy estimation.
      * `"inv"`: Invariant entropy estimation (default).
  * `nbins::Int = 10` (optional): The number of bins for the histogram method. Ignored for other methods. Defaults to 10.
  * `k::Int = 3` (optional): The number of neighbors for the k-NN or invariant method. Ignored for the histogram method. Defaults to 3.
  * `base::Real = e` (optional): The logarithmic base for entropy computation. Defaults to the natural logarithm (`e`).
  * `verbose::Bool = false` (optional): If `true`, prints additional information about the datasets and computation process. Defaults to `false`.
  * `degenerate::Bool = false` (optional): If `true`, adds noise to distances for the k-NN or invariant method to handle degenerate cases. Ignored for the histogram method. Defaults to `false`.
  * `dim::Int = 1` (optional): Indicates whether the data is organized in rows (`dim = 1`) or columns (`dim = 2`). Defaults to 1 (data in rows).
  * `optimize::Bool = false` (optional): If `true`, compute the invariant two-dimensional conditional mutual information of X and Z faster. Defaults to `false`. Y should be nothing.

# Returns

  * `Real`: The computed conditional mutual information I(X; Y | Z)

# Behavior

  * Depending on the specified `method`, the appropriate entropy estimation function (`entropy_knn`, `entropy_hist`, `entropy_inv`) is called.

# Example

x = rand(1, 100)  # 100 points in 1D y = rand(1, 100)  # 100 points in 1D z = rand(1, 100)  # 100 points in 1D

# Using k-NN method

cmi = conditional*mutual*information(x, y, z, method="knn", k=5, verbose=true)

# Using histogram method

cmi = conditional*mutual*information(x, y, z, method="histogram", nbins=10)

# Using invariant method

cmi = conditional*mutual*information(x, y, z, method="inv", k=3)
