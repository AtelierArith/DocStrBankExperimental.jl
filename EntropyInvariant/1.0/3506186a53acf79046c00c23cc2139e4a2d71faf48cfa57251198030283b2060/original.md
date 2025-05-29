```
redundancy(mat_1::Matrix{<:Real}, mat_2::Matrix{<:Real}, mat_3::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

Compute the redundancy of information shared by two datasets X and Y about a third dataset Z using the mutual information between I(X; Z) and I(Y; Z): R(X, Y; Z) = min(I(X; Z), I(Y; Z))

# Arguments

  * `X::Vector or Matrix{<:Real}`: A matrix where each column represents a data point, and each row represents a dimension for the first dataset  X.
  * `Y::Vector or Matrix{<:Real}`: A matrix where each column represents a data point, and each row represents a dimension for the second dataset Y.
  * `Z::Vector or Matrix{<:Real}`: A matrix where each column represents a data point, and each row represents a dimension for the third dataset Z.
  * `method::String = "inv"` (optional): The method to use for mutual information computation. Options are:

      * `"knn"`: k-Nearest Neighbors based mutual information estimation.
      * `"histogram"`: Histogram-based mutual information estimation.
      * `"inv"`: Invariant mutual information estimation (default).
  * `nbins::Int = 10` (optional): The number of bins for the histogram method. Ignored for other methods. Defaults to 10.
  * `k::Int = 3` (optional): The number of neighbors for the k-NN or invariant method. Ignored for the histogram method. Defaults to 3.
  * `base::Real = e` (optional): The logarithmic base for mutual information computation. Defaults to the natural logarithm (`e`).
  * `verbose::Bool = false` (optional): If `true`, prints additional information about the datasets and computation process. Defaults to `false`.
  * `degenerate::Bool = false` (optional): If `true`, adds noise to distances for the k-NN or invariant method to handle degenerate cases. Ignored for the histogram method. Defaults to `false`.
  * `dim::Int = 1` (optional): Indicates whether the data is organized in rows (`dim = 1`) or columns (`dim = 2`). Defaults to 1 (data in rows).

# Returns

  * `Real`: The computed redundancy, defined as the minimum of the mutual information between  X and Z, and Y and Z:

# Behavior

  * Depending on the specified `method`, the appropriate mutual information estimation function (`mutual_information`) is called.

# Example

x = rand(1, 100)  # 100 points in 1D y = rand(1, 100)  # 100 points in 1D z = rand(1, 100)  # 100 points in 1D

# Using k-NN method

redund = redundancy(x, y, z, method="knn", k=5, verbose=true)

# Using histogram method

redund = redundancy(x, y, z, method="histogram", nbins=10)

# Using invariant method

redund = redundancy(x, y, z, method="inv", k=3)
