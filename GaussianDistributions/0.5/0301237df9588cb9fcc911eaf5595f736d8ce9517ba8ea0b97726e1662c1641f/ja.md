```
Gaussian(μ, Σ) -> P
```

平均 `μ` と共分散 `Σ` を持つガウス分布。`rand(P)` と `(log-)pdf(P, x)` を定義します。`Number`、`UniformScaling`、`StaticArrays` および `PSD` 行列と連携するように設計されています。

実装の詳細: `Σ` に対して、関数 `logdet`、`whiten` および `unwhiten`（または後者の2つのフォールバックとして `chol`）が呼び出されます。
