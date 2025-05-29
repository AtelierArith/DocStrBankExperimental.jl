```
fit(config::KncProtoConfig, X, y::CategoricalArray; verbose=true)
fit(config::KncProtoConfig,
    input_clusters::ClusteringData,
    train_X::AbstractVector,
    train_y::CategoricalArray;
    verbose=false
)
```

Creates a KncProto classifier using the given configuration and data.
