```
slicedataset(
    dataset::D,
    dataset_slice::AbstractVector{<:Integer};
    allow_no_instances = false,
    return_view = false,
    kwargs...,
) where {D<:AbstractDataset}
```

Return a machine learning dataset with a subset of the instances.

# Implementation

In order to use slicedataset on a custom dataset representation, provide the following method:     instances(         dataset::D,         dataset*slice::AbstractVector{<:Integer},         return*view::Union{Val{true},Val{false}};         kwargs...     ) where {D<:AbstractDataset}
