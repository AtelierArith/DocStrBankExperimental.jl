```
TaylorFourierTransform.amplitude(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

Hth-harmonic phasorのD次導関数の振幅を取得する関数。

```
∀ h ∈ {0}:
    a₀⁽ᴰ⁾(t) = ξ₀⁽ᴰ⁾(t)
∀ h ∉ {0}:
    aₕ⁽⁰⁾(t) = |2 ⋅ ξₕ⁽⁰⁾(t)| ∈ 𝐑⁺
    aₕ⁽¹⁾(t) = ℜ[2 ⋅ ξₕ⁽¹⁾(t) ⋅ exp(-im ⋅ ϕₕ⁽⁰⁾(t))] ∈ 𝐑
    aₕ⁽²⁾(t) = ℜ[2 ⋅ ξₕ⁽²⁾(t) ⋅ exp(-im ⋅ ϕₕ⁽⁰⁾(t))] + aₕ⁽⁰⁾(t) ⋅ ϕₕ⁽¹⁾(t)² ∈ 𝐑
```

参照: [Assessing Synchrophasor Estimates of an Event Captured by a Phasor  Measurement Unit, pg. 3112](https://ieeexplore.ieee.org/document/9239915)

入力:

  * `sol::AbstractDTFTSolution`   | DTFTソリューション構造体 [-]
  * `D::Int`                      | 導関数の次数 [-], デフォルト=0
  * `H::Int`                      | 調和数 [-], デフォルト=1

出力:

  * `a::Vector{<:Real}`           | 振幅 aₕ⁽ᴰ⁾(t) [?]

```
