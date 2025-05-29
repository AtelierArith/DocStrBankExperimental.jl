```julia
struct LogisticLoss <: MLJLinearModels.AtomicLoss
```

$$
L(x, y) = -∑logσ(xᵢyᵢ)
$$

ここで `logσ` はシグモイド関数の対数です; `yᵢ ∈ {±1}`。ロジスティック回帰において `x` は `Xθ` に対応し、ここで `X` はデザイン行列、`θ` はパラメータのベクトルです。[`logsigmoid`](@ref)を参照してください。
