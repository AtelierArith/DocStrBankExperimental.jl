```
samplevisible(rbm, h)
samplevisible(rbm, h, factor)
```

AbstractRBM `rbm` の可視ノードの活性化を返し、隠れノードの状態 `h` からサンプリングされます。`h` はベクトルまたは行にサンプルを含む行列である可能性があります。`factor` については、`visiblepotential(rbm, h, factor)` を参照してください。
