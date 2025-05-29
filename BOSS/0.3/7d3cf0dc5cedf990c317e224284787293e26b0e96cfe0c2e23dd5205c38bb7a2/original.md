```
augment_dataset!(data::ExperimentDataPost, x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
augment_dataset!(data::ExperimentDataPost, X::AbstractMatrix{<:Real}, Y::AbstractMatrix{<:Real})
```

Add one (as vectors) or more (as matrices) datapoints to the dataset.
