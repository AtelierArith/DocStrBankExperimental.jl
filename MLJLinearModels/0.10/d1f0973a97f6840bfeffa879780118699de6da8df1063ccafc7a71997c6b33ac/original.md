```julia
struct MultinomialLoss{c} <: MLJLinearModels.MultiClassLoss{c}
```

$L(P, y) = ∑log Zᵢ - ∑∑ 1(yᵢ=j)Pᵢⱼ$

where `P` is a matrix where each row contains class probabilities, `yᵢ ∈ {1, 2, ..., K}` corresponding to column indices and,

$Zᵢ = ∑ exp(Pᵢ)$

In a multinomial regression, `P` corresponds to `XW` where `X` is the design matrix and `W` the matrix of size `p × K` where each column corresponds to the parameters corresponding to that class.
