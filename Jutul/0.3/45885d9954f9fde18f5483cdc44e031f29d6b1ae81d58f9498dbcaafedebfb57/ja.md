```
simulate(state0, sim::JutulSimulator, timesteps::AbstractVector; parameters = nothing, kwarg...)
```

与えられた初期状態 `state0` に対して、`simulator` で指定された `timesteps` のセットをシミュレートし、オプションで特定のパラメータを指定します。
