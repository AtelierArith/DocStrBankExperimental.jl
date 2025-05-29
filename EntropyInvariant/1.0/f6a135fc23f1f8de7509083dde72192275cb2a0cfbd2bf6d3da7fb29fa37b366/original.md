```
normalized_mutual_information(mat_1::Matrix{<:Real}, mat_2::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

Compute the normalized mutual information (NMI) between two datasets as  NMI(X, Y) = max(0, H(X) + H(Y) - H(X, Y))/(H(X) + H(Y)   where:

  * H(X): Entropy of the first dataset X.
  * H(Y): Entropy of the second dataset Y`
  * H(X, Y): Joint entropy of X and Y.

# Arguments

  * X::Vector or Matrix{<:Real}`: A matrix where each column represents a data point and each row represents a dimension for the first dataset.
  * Y::Vector or Matrix{<:Real}`: A matrix where each column represents a data point and each row represents a dimension for the second dataset.
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

# Returns

  * `Real`: The normalized mutual information NMI(X, Y) between X and Y.

      * 0 < NMI < 1, where 0 indicates no shared information and 1 indicates complete mutual information.

# Behavior

  * Depending on the specified `method`, the appropriate entropy estimation function (`entropy_knn`, `entropy_hist`, `entropy_inv`) is called.

# Example

x = rand(1, 100)  # 100 points in 1D y = rand(1, 100)  # 100 points in 1D

# Using k-NN method

nmi = normalized*mutual*information(x, y, method="knn", k=5, verbose=true)

# Using histogram method

nmi = normalized*mutual*information(x, y, method="histogram", nbins=10)

# Using invariant method

nmi = normalized*mutual*information(x, y, method="inv", k=3)
