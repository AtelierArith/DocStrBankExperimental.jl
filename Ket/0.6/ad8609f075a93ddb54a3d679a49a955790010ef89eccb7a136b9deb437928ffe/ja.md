```
relative_entropy([base=2,] ρ::AbstractMatrix, σ::AbstractMatrix)
```

正定行列 `ρ` と `σ` の間の (量子) 相対エントロピー tr(`ρ` (log `ρ` - log `σ`)) を、基数 `base` の対数を使用して計算します。`ρ` のサポートは `σ` のサポートに含まれている必要がありますが、効率のためにこれはチェックされません。

参考文献: [量子相対エントロピー](https://en.wikipedia.org/wiki/Quantum_relative_entropy)
