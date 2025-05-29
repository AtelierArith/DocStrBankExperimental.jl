```
Oblimin(; gamma, orthogonal = false)
```

*Oblimin*回転法のファミリー。

## キーワード引数

  * `gamma`: 回転基準を決定する形状パラメータ（*詳細*を参照）。
  * `orthogonal`: `orthogonal = true`の場合は直交回転が行われ、それ以外の場合は斜交回転が行われます。（デフォルト: `false`）

## 詳細

*Oblimin*回転ファミリーは、次の基準を最小化する直交回転と斜交回転の両方を許可します：

$$
\begin{aligned}
Q_{\mathrm{oblimin}}(Λ, γ) =&
    \frac{1}{4} \left⟨Λ², \left(I - \frac{γ}{p} 1^{p\times p}\right) ⋅
                             Λ² ⋅ \left(1^{k\times k} - I\right) \right⟩ = \\
  & = \frac{1}{4} ∑_{i=1}^p \left(∑_{j=1}^k λ²_{i, j}\right)²
    + \frac{γ}{4p} ∑_{j=1}^k \left(∑_{i=1}^p λ²_{i, j}\right)²
    - \frac{γ}{4p} \left(∑_{i, j} λ²_{i, j}\right)²
    - \frac{1}{4} ∑_{i, j} λ⁴_{i, j}.
\end{aligned}
$$

この基準の定義は、*共通性*を保持する負荷行列の回転の場合に与えられています（[斜交回転](@ref rotation_oblique）を参照）。任意の回転行列には適用されません。

直交回転が行われる場合、*Oblimin*は`gamma`の値に対して次の回転法と同等です：

  * *γ = p×ϰ*: [`CrawfordFerguson(kappa = ϰ, orthogonal = true)`](@ref CrawfordFerguson)
  * *γ = 0*: [`Quartimax`](@ref)
  * *γ = 1/2*: [`Biquartimax`](@ref)
  * *γ = 1*: [`Varimax`](@ref)
  * *γ = k/2*: [`Equamax`](@ref)
  * *γ = p×(k - 1)/(p + k - 2)*: [`Parsimax`](@ref)

斜交回転の場合、*Oblimin*は次の回転法と同等です：

  * *γ = 0*: *Quartimin*
  * *γ = 1/2*: [`Biquartimin`](@ref)

## 例

```jldoctest
julia> Oblimin(gamma = 0.5)
Oblimin{Oblique, Float64}(0.5)

julia> Oblimin(gamma = 1, orthogonal = true)
Oblimin{Orthogonal, Int64}(1)
```
