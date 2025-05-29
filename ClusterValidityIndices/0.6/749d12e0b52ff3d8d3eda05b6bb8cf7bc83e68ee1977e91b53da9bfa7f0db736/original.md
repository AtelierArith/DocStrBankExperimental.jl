Main module for `ClusterValidityIndices.jl`, a Julia package of metrics for unsupervised learning.

This module exports all of the CVI modules, options, and utilities used by the `ClusterValidityIndices.jl` package. For full usage, see the official guide at https://ap6yc.github.io/ClusterValidityIndices.jl/dev/man/guide/.

# Basic Usage

Install and import the package in a script with

```julia
using Pkg
Pkg.add("ClusterValidityIndices")
using ClusterValidityIndices
```

then create a CVI object with an empty argument constructor

```julia
my_cvi = DB()
```

and get the criterion values with `get_cvi!` (batch) or `get_icvi!` (incremental)

```julia
# Load some features and labels from a clustering process
features, labels = get_some_clustering_data()

# Batch criterion value
criterion_value = get_cvi!(my_cvi, features, labels)

# Incremental criterion values
criterion_values = zeros(length(labels))
for ix in eachindex(labels)
    criterion_values[ix] = get_icvi!(my_cvi, features[:, ix], labels[ix])
end
```

# Imports

The following names are imported by the package as dependencies:

  * `Base`
  * `Core`
  * `DocStringExtensions`
  * `ElasticArrays`
  * `LinearAlgebra`
  * `NumericalTypeAliases`
  * `Pkg`

# Exports

The following names are exported and available when `using` the package:

  * [`CH`](@ref)
  * [`CLUSTERVALIDITYINDICES_VERSION`](@ref)
  * [`CVI`](@ref)
  * [`CVI_MODULES`](@ref)
  * [`DB`](@ref)
  * [`GD43`](@ref)
  * [`GD53`](@ref)
  * [`PS`](@ref)
  * [`WB`](@ref)
  * [`XB`](@ref)
  * [`cSIL`](@ref)
  * [`get_cvi!`](@ref)
  * [`rCIP`](@ref)
