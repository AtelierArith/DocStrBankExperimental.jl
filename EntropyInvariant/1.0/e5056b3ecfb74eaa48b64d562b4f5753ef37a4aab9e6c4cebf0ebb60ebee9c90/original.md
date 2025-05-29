```
entropy(X::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

Compute the entropy of a dataset using one of several methods.

# Arguments

  * `X::Vector or Matrix{<:Real}`: A matrix where each column represents a data point, and each row represents a dimension.
  * `method::String = "inv"` (optional): The method to use for entropy computation. Options are:

      * `"knn"`: k-Nearest Neighbors (k-NN) based entropy estimation.
      * `"histogram"`: Histogram-based entropy estimation.
      * `"inv"`: Invariant entropy estimation (default).
  * `nbins::Int = 10` (optional): The number of bins for the histogram method. Ignored for other methods. Defaults to 10.
  * `k::Int = 3` (optional): The number of neighbors for the k-NN or invariant method. Ignored for the histogram method. Defaults to 3.
  * `base::Real = e` (optional): The logarithmic base for entropy computation. Defaults to the natural logarithm (`e`).
  * `verbose::Bool = false` (optional): If `true`, prints additional information about the dataset and computation process. Defaults to `false`.
  * `degenerate::Bool = false` (optional): If `true`, adds noise to distances for the k-NN or invariant method to handle degenerate cases. Ignored for the histogram method. Defaults to `false`.
  * `dim::Int = 1` (optional): Indicates whether the data is organized in rows (`dim = 1`) or columns (`dim = 2`). Defaults to 1 (data in rows).

# Returns

  * `Real`: The computed entropy of the dataset.

# Behavior

  * The function chooses the entropy estimation method based on the `method` argument:

    1. **k-NN Method** (`method = "knn"`):

          * Estimates entropy based on nearest-neighbor distances.
    2. **Histogram Method** (`method = "histogram"`):

          * Estimates entropy using a histogram of the data.
    3. **Invariant Method** (`method = "inv"`):

          * Estimates entropy with invariant scaling properties using nearest neighbors.
  * The appropriate entropy function (`entropy_knn`, `entropy_hist`, or `entropy_inv`) is called based on the specified method.

# Example

# Using k-NN method

data = rand(1, 100)  # 100 points in 1 dimension println("Entropy (k-NN): ", entropy(data, method="knn", k=5, verbose=true))

# Using histogram method

data = rand(100)  # 100 points in 1 dimension println("Entropy (Histogram): ", entropy(data, method="histogram", nbins=10) )

# Using invariant method

println("Entropy (Invariant): ", entropy(data, method="inv", k=3))
