```
spectral_mixture_product_kernel(
    h::Kernel=SqExponentialKernel(),
    αs::AbstractMatrix{<:Real},
    γs::AbstractMatrix{<:Real},
    ωs::AbstractMatrix{<:Real},
)
```

ここで、αsは次元(D, A)の重み、γsは次元(D, A)の共分散行列、ωsは次元(D, A)の平均ベクトルです。ここで、Dは入力次元、Aはスペクトル成分の数です。

スペクトル混合積カーネル。十分な成分Aを持つことで、SMPカーネルは任意の積カーネルを任意の精度でモデル化でき、小さな数の成分でも柔軟です [1]

`h`はカーネルで、指定されていない場合は[`SqExponentialKernel`](@ref)がデフォルトとなります。

$$
   κ(x, y) = Πᵢ₌₁ᴷ Σ(αsᵢᵀ .* (h(-(γsᵢᵀ * tᵢ)²) .* cos(ωsᵢᵀ * tᵢ))), tᵢ = xᵢ - yᵢ
$$

# 参考文献:

```
[1] GPatt: Fast Multidimensional Pattern Extrapolation with GPs,
    arXiv 1310.5288, 2013, by Andrew Gordon Wilson, Elad Gilboa,
    Arye Nehorai and John P. Cunningham
```
