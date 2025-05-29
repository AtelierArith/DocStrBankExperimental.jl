```
build_clusters!(index::AbstractDocumentIndex, cls::TrainedClassifier;
    topic_level::AbstractString = "",
    verbose::Bool = true, add_label::Bool = false, add_summary::Bool = false,
    labeler_kwargs::NamedTuple = NamedTuple())
```

Builds topics based on the classifier's labels and labels all documents in the `index` with the highest probability label.

# Example

```julia
# Assume `index` is already built and so is classifier `cls`
build_clusters!(index, cls; topic_level = "MyClusters")

# Check that our new topic level is available
topic_levels(index) |> keys
```
