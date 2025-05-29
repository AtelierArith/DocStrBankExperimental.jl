```
GroupViaNearestFeature(templates; kwargs...)
```

Initialize a struct that contains instructions on how to group features in [`AttractorsViaFeaturizing`](@ref). `GroupViaNearestFeature` accepts a `template`, which is a vector of features. Then, generated features from initial conditions in [`AttractorsViaFeaturizing`](@ref) are labelled according to the feature in `templates` that is closest (the label is the index of the closest template).

`templates` can be a vector or dictionary mapping keys to templates. Internally all templates are converted to `SVector` for performance. Hence, it is strongly recommended that both `templates` and the output of the `featurizer` function in [`AttractorsViaFeaturizing`](@ref) return `SVector` types.

## Keyword arguments

  * `metric = Euclidean()`: metric to be used to quantify distances in the feature space.
  * `max_distance = Inf`: Maximum allowed distance between a feature and its nearest template for it to be assigned to that template. By default, `Inf` guarantees that a feature is assigned to its nearest template regardless of the distance. Features that exceed `max_distance` to their nearest template get labelled `-1`.
