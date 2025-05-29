```julia
get_cvi!(
    cvi::ClusterValidityIndices.CVI,
    sample::AbstractVector{T} where T<:Real,
    label::Integer
) -> Any

```

# Summary

Compute and return the criterion value incrementally.

This method takes the CVI object, a single sample as a vector of floats, and a single integer that represents the label prescribed to the sample by your clustering algorithm.

!!! note
    You cannot switch to batch mode after incrementally evaluating a CVI. To evaluate in batch, you much create a new CVI object.


# Arguments

  * `cvi::CVI`: the stateful information of the ICVI providing the criterion value.
  * `sample::RealVector`: a vector of features used in clustering the sample.
  * `label::Integer`: the cluster label prescribed to the sample by the clustering algorithm.

# Examples

```julia
# Create a new CVI object
my_cvi = CH()

# Load in random data as an example; 10 samples with feature dimenison 3
dim = 3
n_samples = 10
data = rand(dim, n_samples)
labels = repeat(1:2, inner=n_samples)

# Iteratively compute and extract the criterion value at every step
criterion_values = zeros(n_samples)
for ix = 1:n_samples
    sample = data[:, ix]
    label = labels[ix]
    criterion_values[ix] = get_icvi!(my_cvi, sample, label)
end
```

# Method List / Definition Locations

```julia
get_cvi!(cvi, sample, label)
```

defined at [`packages/ClusterValidityIndices/UT9rS/src/common.jl:392`](file:///home/terasaki/.julia/packages/ClusterValidityIndices/UT9rS/src/common.jl).
