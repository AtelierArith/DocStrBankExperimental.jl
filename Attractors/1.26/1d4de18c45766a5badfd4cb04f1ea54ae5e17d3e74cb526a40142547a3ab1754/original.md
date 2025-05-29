```
group_features(features, group_config::GroupingConfig) → labels
```

Group the given iterable of "features" (anything that can be grouped, typically vectors of real numbers) according to the configuration and return the labels (vector of equal length as `features`). See [`GroupingConfig`](@ref) for possible grouping configuration configurations.
