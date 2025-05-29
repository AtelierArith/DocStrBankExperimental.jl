```
sample(pc::ProbCircuit, num_samples, data::Matrix;; batch_size, rng = default_rng())
```

回路の条件付きでの結合分布から `num_samples` を生成します。
