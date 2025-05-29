```
sample(pc::ProbCircuit, num_samples; rng = default_rng())
```

条件なしで回路の同時分布から `num_samples` を生成します。サンプルはCPU上で生成されます。
