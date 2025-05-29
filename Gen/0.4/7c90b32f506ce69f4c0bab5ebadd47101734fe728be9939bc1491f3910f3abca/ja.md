```
traces::Vector = sample_unweighted_traces(state::ParticleFilterState, num_samples::Int)
```

与えられた粒子フィルタ状態の重み付きトレースコレクションから `num_samples` トレースのベクトルをサンプリングします。
