```
GammaExponentialKernel(; γ::Real=1.0, metric=Euclidean())
```

γ-指数カーネルは、`metric`に関して、パラメータ`γ`を持ちます。

# 定義

入力$x, x'$およびメトリック$d(\cdot, \cdot)$に対して、パラメータ$\gamma \in (0, 2]$を持つγ-指数カーネル[^RW]は次のように定義されます。

$$
k(x, x'; \gamma) = \exp\big(- d(x, x')^{\gamma}\big).
$$

デフォルトでは、$d$はユークリッドメトリック$d(x, x') = \|x - x'\|_2$です。

関連情報: [`ExponentialKernel`](@ref), [`SqExponentialKernel`](@ref)

[^RW]: C. E. Rasmussen & C. K. I. Williams (2006). Gaussian Processes for Machine Learning.
