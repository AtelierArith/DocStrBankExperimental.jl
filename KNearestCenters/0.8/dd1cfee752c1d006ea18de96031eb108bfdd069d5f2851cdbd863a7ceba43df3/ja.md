```
fit(config::KncProtoConfig, X, y::CategoricalArray; verbose=true)
fit(config::KncProtoConfig,
    input_clusters::ClusteringData,
    train_X::AbstractVector,
    train_y::CategoricalArray;
    verbose=false
)
```

指定された構成とデータを使用してKncProto分類器を作成します。
