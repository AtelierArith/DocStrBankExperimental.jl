```
TaylorFourierTransform.ar_phase(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

D次導関数のH次ハーモニック位相の反回転位相を取得する関数。

```
∀ h ∈ {0}:
    φ₀⁽ᴰ⁾(t) = 0.0
∀ h ∉ {0}:
    φₕ⁽⁰⁾(t) = ∠[ψₕ⁽⁰⁾(t)] ∈ [-π,π]
    φₕ⁽¹⁾(t) = ℑ[2 ⋅ ψₕ⁽¹⁾(t) ⋅ exp(-im ⋅ φₕ⁽⁰⁾(t))] / aₕ⁽⁰⁾(t) ∈ 𝐑
    φₕ⁽²⁾(t) = {ℑ[2 ⋅ ψₕ⁽²⁾(t) ⋅ exp(-im ⋅ φₕ⁽⁰⁾(t))] - 2 ⋅ aₕ⁽¹⁾(t) ⋅ φₕ⁽¹⁾(t)} / aₕ⁽⁰⁾(t) ∈ 𝐑
```

参照: [Assessing Synchrophasor Estimates of an Event Captured by a Phasor  Measurement Unit, pg. 3112](https://ieeexplore.ieee.org/document/9239915)

入力:

  * `sol::AbstractDTFTSolution`   | DTFTソリューション構造体 [-]
  * `D::Int`                      | 導関数の次数 [-], デフォルト=0
  * `H::Int`                      | ハーモニック番号 [-], デフォルト=1

出力:

  * `φ::Vector{<:Real}`           | 反回転位相 φₕ⁽ᴰ⁾(t) [(rad)]
