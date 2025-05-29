```
CrawfordFerguson(; kappa, orthogonal = false)
```

*クロフォード・ファーガソン*回転法のファミリー。

## キーワード引数

  * `kappa`: 回転基準を決定するパラメータ（*詳細*を参照）。
  * `orthogonal`: orthogonal: orthogonal = true の場合は直交回転が行われ、それ以外は斜交回転が行われます。（デフォルト: `false`）

## 詳細

*クロフォード・ファーガソン*ファミリーは、以下の基準に従って因子負荷行列の直交回転と斜交回転の両方を許可します：

$$
\begin{aligned}
Q_{\mathrm{CF}}(Λ, ϰ) &=
    \frac{1 - ϰ}{4} \left⟨Λ², Λ²⋅\left(1^{k×k} - I\right) \right⟩ +
    \frac{ϰ}{4} \left⟨Λ², (1^{p×p} - I)⋅Λ²\right⟩ = \\
  &\hspace{4em} = -\frac{1 - ϰ}{4} k ∑_{i=1}^p \mathrm{Var}(Λ²_{i, \cdot})
    - \frac{ϰ}{4} p ∑_{j=1}^k \mathrm{Var}(Λ²_{⋅, j}) = \\
  &\hspace{8em} = \frac{1 - ϰ}{4} ∑_{i=1}^p \left(∑_{j=1}^k λ_{i,j}² \right)²
    + \frac{ϰ}{4} ∑_{j=1}^k \left(∑_{i=1}^p λ_{i,j}² \right)²
    - \frac{1}{4} ∑_{i,j} λ⁴_{i,j}.
\end{aligned}
$$

回転が*直交*の場合、*共通性*（$c_i = ∑_{j=1}^k λ_{i,j}²$）が保持され、特定の`kappa`に対して、クロフォード・ファーガソン基準は以下の回転法と同等になります：

  * *ϰ = γ/p*: [`Oblimin(gamma = γ, orthogonal = true)`](@ref Oblimin)
  * *ϰ = 0*: [`Quartimax`](@ref)
  * *ϰ = 1/p*: [`Varimax`](@ref)
  * *ϰ = k/2p*: [`Equamax`](@ref)
  * *ϰ = (k - 1)/(p + k - 2)*: [`Parsimax`](@ref)
  * *ϰ = 1*: 因子の簡潔さ

## 例

```jldoctest
julia> CrawfordFerguson(kappa = 0, orthogonal = true)
CrawfordFerguson{Orthogonal, Int64}(0)

julia> CrawfordFerguson(kappa = 1/2, orthogonal = false)
CrawfordFerguson{Oblique, Float64}(0.5)
```
