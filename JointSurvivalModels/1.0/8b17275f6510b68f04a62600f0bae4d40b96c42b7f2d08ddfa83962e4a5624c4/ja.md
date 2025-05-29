```
JointSurvivalModel <: HazardBasedDistribution <: ContinuousUnivariateDistribution
```

`JointSurvivalModel`はハザードの定式化に基づいています：

$$
h_i(t) = h_0(t) \exp\left(\gamma' \cdot L(M_i (t)) + \beta' \cdot x \right),
$$

ここで、$h_0: \mathbb{R} \to \mathbb{R}_{+}$はベースラインハザード関数です。項$L(M(t)): \mathbb{R} \to \mathbb{R}^k, k\in\mathbb{N}$は縦断的モデルへのリンクを表し、$\gamma\in\mathbb{R}^k$はリンク係数です。最後に、$x \in\mathbb{R}^l, l\in\mathbb{N}$は係数$\beta\in\mathbb{R}^l$を持つ共変量です。

# フィールド：

  * `h₀::Function`: ベースラインハザードを表す時間における正の値の関数
  * `γ::Vector{Real}`: 縦断的モデルへのリンクの係数、`link_m`と同じ長さである必要があります
  * `link_m::Vector{Function}`: 単一または複数の縦断的モデルへのリンクを表す時間における単項関数（1つの引数）
  * `β::Vector{Real}`: 共変量の係数、`x`と同じ長さである必要があります
  * `x::Vector{Real}`: 共変量

# 例

共変量なしで`JointSurvivalModel`を呼び出すためのコンストラクタや、配列を必要としない単一の縦断的モデルのためのコンストラクタがあります。例えば：

```
using JointSurvivalModels

JointSurvivalModel(identity, 0.01, identity, 0.02, 3)
# ハザードに対応: identity(t) * exp(0.01 * identity(t) +  0.02 * 3) 
JointSurvivalModel(identity, 0.01, identity)
# ハザードに対応: identity(t) * exp(0.01 * identity(t))
JointSurvivalModel(identity,
                    [0.01,-0.02,0.03],
                    [x -> sqrt(x), x -> sin(x)+1, x -> cos(x)^2],
                    [2, 0.3],
                    [ 0, sqrt(2)])
# ハザードに対応: identity(t) * exp(0.01 * sqrt(t) - 0.02 * (sin(t)+1) + 0.03 * cos(t)^2  + 2 * 0 + 0.3 * sqrt(2))
```
