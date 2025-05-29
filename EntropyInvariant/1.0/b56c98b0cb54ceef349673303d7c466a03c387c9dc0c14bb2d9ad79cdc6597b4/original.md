```
unique(mat_1::Matrix{<:Real}, mat_2::Matrix{<:Real}, mat_3::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Tuple{Real, Real}
```

Compute the unique information that two datasets X and Y contribute individually about a third dataset Z as: U(X; Z) = I(X; Z) - R(X, Y; Z) U(Y; Z) = I(Y; Z) - R(X, Y; Z) where:

  * R(X, Y; Z) = min(I(X; Z), I(Y; Z)) si the Redundancy of  X and Y about Z.

# Arguments

  * `X::Vector or Matrix{<:Real}`: A matrix where each column represents a data point, and each row represents a dimension for the first dataset X.
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

  * `Tuple{Real, Real}`: A tuple (U(X; Z), U(Y; Z)).

# Behavior

  * Depending on the specified `method`, the appropriate mutual information estimation function (`mutual_information`) is called.

# Example

x = rand(1, 100)  # 100 points in 1D y = rand(1, 100)  # 100 points in 1D z = rand(1, 100)  # 100 points in 1D

# Using k-NN method

unique*x, unique*y = unique(x, y, z, method="knn", k=5, verbose=true)

# Using histogram method

unique*x, unique*y = unique(x, y, z, method="histogram", nbins=10)

# Using invariant method

unique*x, unique*y = unique(x, y, z, method="inv", k=3)
