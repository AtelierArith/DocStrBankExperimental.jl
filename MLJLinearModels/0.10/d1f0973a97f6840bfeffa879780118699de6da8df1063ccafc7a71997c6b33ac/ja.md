```julia
struct MultinomialLoss{c} <: MLJLinearModels.MultiClassLoss{c}
```

$$
L(P, y) = ∑log Zᵢ - ∑∑ 1(yᵢ=j)Pᵢⱼ
$$

ここで、`P`は各行がクラス確率を含む行列であり、`yᵢ ∈ {1, 2, ..., K}`は列インデックスに対応し、

$$
Zᵢ = ∑ exp(Pᵢ)
$$

多項式回帰において、`P`は`XW`に対応し、ここで`X`はデザイン行列、`W`はサイズ`p × K`の行列であり、各列はそのクラスに対応するパラメータに対応します。
