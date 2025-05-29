```
mutual_information(X::Matrix{<:Real}, Y::Union{Matrix{<:Real}, Nothing} = nothing; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1, optimize::Bool = false) -> Real
```

Compute the mutual information between two datasets as I(X; Y) = H(X) + H(Y) - H(X, Y)   where:

  * H(X): Entropy of the first dataset X.
  * H(Y): Entropy of the second dataset Y.
  * H(X, Y): Joint entropy of X and Y.

# Arguments

  * X::Vector or Matrix{<:Real}`: A matrix where each column represents a data point, and each row represents a dimension for the first dataset.
  * Y::Vector or Matrix{<:Real}`: A matrix where each column represents a data point, and each row represents a dimension for the second dataset.
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
  * `optimize::Bool = false` (optional): If `true`, compute the invariant two-dimensional mutual_information of X faster. Defaults to `false`. Y should be nothing.

# Returns

  * `Real`: The computed mutual information I(X; Y) between the datasets X and Y.

# Behavior

  * Depending on the specified `method`, the appropriate entropy estimation function (`entropy_knn`, `entropy_hist`, `entropy_inv`) is called.

# Example

x = rand(1, 100)  # 100 points in 1D y = rand(1, 100)  # 100 points in 1D

# Using histogram kNN method

mi = mutual_information(x, y, method="knn", k=5, verbose=true)

# Using histogram method

mi = mutual_information(x, y, method="histogram", nbins=10)

# Using invariant method

mi = mutual_information(x, y, method="inv", k=3)
