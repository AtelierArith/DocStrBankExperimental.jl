```
update!(
    P::Predictor,
    H::AbstractHomotopy,
    x,
    t,
    jacobian::Jacobian,
    norm::AbstractNorm,
    x̂ = nothing,
)
```

新しい解 `(x,t)` を用いて予測器を更新します。これは新しい局所微分を計算し、適切な予測方法を選択します。
