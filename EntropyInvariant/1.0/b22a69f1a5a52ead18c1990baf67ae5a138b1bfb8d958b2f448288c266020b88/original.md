```
interaction_information(mat_1::Matrix{<:Real}, mat_2::Matrix{<:Real}, mat_3::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3,base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

Compute the interaction information (II) between three datasets as II(X; Y; Z) = H(X) + H(Y) + H(Z) - H(X, Y) - H(X, Z) - H(Y, Z) + H(X, Y, Z)   where:

  * H(X), H(Y), H(Z): Entropies of the individual datasets.
  * H(X, Y), H(X, Z), H(Y, Z): Pairwise joint entropies.
  * H(X, Y, Z): Joint entropy of all three datasets.

# Arguments

  * `X::Vector or Matrix{<:Real}`: A matrix where each column represents a data point and each row represents a dimension for the first dataset.
  * `Y::Vector or Matrix{<:Real}`: A matrix where each column represents a data point and each row represents a dimension for the second dataset.
  * `Z::Vector or Matrix{<:Real}`: A matrix where each column represents a data point and each row represents a dimension for the third dataset.
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

  * `Real`: The computed interaction information II(X; Y; Z) between the datasets X, Y and Z.

# Behavior

  * Depending on the specified `method`, the appropriate entropy estimation function (`entropy_knn`, `entropy_hist`, `entropy_inv`) is called.

# Example

x = rand(1, 100)  # 100 points in 1D y = rand(1, 100)  # 100 points in 1D z = rand(1, 100)  # 100 points in 1D

# Using k-NN method

ii = interaction_information(x, y, z, method="knn", k=5, verbose=true)

# Using histogram method

ii = interaction_information(x, y, z, method="histogram", nbins=10)

# Using invariant method

ii = interaction_information(x, y, z, method="inv", k=3)
