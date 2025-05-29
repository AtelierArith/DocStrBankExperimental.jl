```julia
load_dataset(name; kwargs...)

```

Will load the dataset `dataset_name` and, in this order and depending on keyword arguments, center it (substract mean), standardize it (divide each attribute by its std) and then rescale the samples (so that maximum ‖xᵢ‖₂ is 1.0).

Keyword arguments include:

  * center = false
  * standardize = false
  * rescale_columns = false

For HDF5-based datasets, one can also specify:

  * ncols = Inf: a number of columns to use for the dataset.

Note that dataset statistics need to be recomputed each time when using `ncols` together with `center`, `standardize` ou `rescale_columns`.
