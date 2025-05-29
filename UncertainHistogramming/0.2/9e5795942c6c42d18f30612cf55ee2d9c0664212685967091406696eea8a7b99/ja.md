```
GaussianHistogram{T <: Number} <: ContinuousHistogram
```

各値-誤差ペアに対してガウスカーネルを持つ[`ContinuousHistogram`](@ref)。

この[`ContinuousHistogram`]は、各$(\mu_i, \sigma_i)$に対してガウスカーネルを合計することによって形成されます。

$$
\mathcal{H}(y) = \frac{1}{M} \sum_{i = 1}^M G(y; \mu_i, \sigma_i),
$$

ここで

$$
G(y; \mu_i, \sigma_i) = \frac{ \exp\left[ -\frac{ \left( y - \mu_i \right)^2 }{2 \sigma_i^2} \right] }{ \sigma_i \sqrt{2\pi}}.
$$

この式は、非中心の[`moment`](@ref)の計算を、個々の非中心の[`moment`](@ref)の単純な平均にします。

# 目次

  * `moments::Vector{T}`: `GaussianHistogram`のためのモーメントのコレクションで、*オンライン*方式で更新されます
  * `values::Vector{T}`: `GaussianHistogram`を[`construct`](@ref)するために使用される値
  * `errors::Vector{T}`: `GaussianHistogram`を[`construct`](@ref)するために使用される誤差

!!! note
    統計は[`moment`](@ref)に関する計算から得られます。`values`と`errors`は視覚化の目的で必ず保存されます。

