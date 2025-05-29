```
TaylorFourierTransform.phase(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

D次導関数のH次ハーモニック位相の代替角を取得する関数。

```
∀ h ∈ {0}:
    ϕ₀⁽ᴰ⁾(t) = 0.0
∀ h ∉ {0}:
    ϕₕ⁽⁰⁾(t) = ∠[pₕ⁽⁰⁾(t)] ∈ [-π,π]
    ϕₕ⁽¹⁾(t) = ℑ[2 ⋅ ξₕ⁽¹⁾(t) ⋅ exp(-im ⋅ ϕₕ⁽⁰⁾(t))] / aₕ⁽⁰⁾(t) ∈ 𝐑
    ϕₕ⁽²⁾(t) = {ℑ[2 ⋅ ξₕ⁽²⁾(t) ⋅ exp(-im ⋅ ϕₕ⁽⁰⁾(t))] - 2 ⋅ aₕ⁽¹⁾(t) ⋅ ϕₕ⁽¹⁾(t)} / aₕ⁽⁰⁾(t) ∈ 𝐑
```

参照: [Assessing Synchrophasor Estimates of an Event Captured by a Phasor  Measurement Unit, pg. 3112](https://ieeexplore.ieee.org/document/9239915)

入力:

  * `sol::AbstractDTFTSolution`   | DTFTソリューション構造体 [-]
  * `D::Int`                      | 導関数の次数 [-], デフォルト=0
  * `H::Int`                      | ハーモニック番号 [-], デフォルト=1

出力:

  * `ϕ::Vector{<:Real}`           | 位相 ϕₕ⁽ᴰ⁾(t) [(rad)]
