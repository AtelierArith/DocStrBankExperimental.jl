```
loglikelihoods(pc::ProbCircuit, data::Matrix)
```

`circuit`の`data`に対する対数尤度を計算します。回路を線形化し、バッチで周辺分布を計算します。
