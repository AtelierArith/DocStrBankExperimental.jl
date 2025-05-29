```
samplehidden(rbm, v)
samplehidden(rbm, v, factor)
```

AbstractRBM `rbm` の隠れノードの活性化を、可視ノードの状態 `v` からサンプリングして返します。`v` はベクトルまたは行にサンプルを含む行列である可能性があります。`factor` については、`hiddenpotential(rbm, v, factor)` を参照してください。
