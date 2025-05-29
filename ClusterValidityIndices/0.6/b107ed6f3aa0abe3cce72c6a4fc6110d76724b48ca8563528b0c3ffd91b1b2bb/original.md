```julia
get_cvi!(
    cvi::ClusterValidityIndices.CVI,
    data::AbstractMatrix{T} where T<:Real,
    labels::AbstractVector{T} where T<:Integer
) -> Any

```

# Summary

Compute and return the criterion value in batch mode.

This method takes the CVI object, a batch of samples as a matrix of floats, and a vector of integers that represent the labels prescribed to the data by your clustering algorithm.

!!! note
    You cannot switch to incremental mode after evaluating a CVI in batch mode. To evaluate incrementally, you much create a new CVI object.


# Arguments

  * `cvi::CVI`: the stateful information of the CVI providing the criterion value.
  * `data::RealMatrix`: a matrix of data, columns as samples and rows as features, used in the external clustering process.
  * `labels::IntegerVector`: a vector of integers representing labels prescribed to the `data` by the external clustering algorithm.

# Examples

```julia
# Create a new CVI object
my_cvi = CH()

# Load in random data as an example; 10 samples with feature dimenison 3
dim = 3
n_samples = 10
data = rand(dim, n_samples)
labels = repeat(1:2, inner=n_samples)

# Compute the final criterion value in batch mode
criterion_value = get_cvi!(cvi, data, labels)
```

# Method List / Definition Locations

```julia
get_cvi!(cvi, data, labels)
```

defined at [`packages/ClusterValidityIndices/UT9rS/src/common.jl:432`](file:///home/terasaki/.julia/packages/ClusterValidityIndices/UT9rS/src/common.jl).
