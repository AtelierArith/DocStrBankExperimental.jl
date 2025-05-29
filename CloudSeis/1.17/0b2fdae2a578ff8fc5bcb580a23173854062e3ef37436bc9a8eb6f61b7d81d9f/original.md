```
description!(io::CSeis, kwargs...)
```

Limited mutation of the properties of an existing CloudSeis dataset.

# Optional key-word arguments

  * `axis_lengths = nothing`  Grow the size of the axis lengths (3rd dimension and higher)[1].
  * `dataproperties = nothing` Replace the data properties of the dataset with `dataproperties`.[2]
  * `dataproperties_add = nothing` Add to the data properties of the dataset with `dataproperties_add`.[2]

# Notes

  * [1] `axis_lengths` must be the same length as `size(io)`.  In addition, `prod(axis_lengths[3:end])`

must be greater than `prod(size(io)[3:end])` and `axis_lengths[i]` must equal `size(io,i)` for i∈(1..ndims(io)-1).

  * [2] only one of `dataproperties` or `dataproperties_add` can be specified.
