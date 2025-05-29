```
TaylorFourierTransform.ar_phasor(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

H次調和のD次導関数を取得するための関数。

```
∀ h ∈ {0}:
    ψ₀⁽ᴰ⁾(t) = ξ₀⁽ᴰ⁾(t) ∈ ℝ
∀ h ∉ {0}:
    ψₕ⁽ᴰ⁾(t) = ξₕ⁽ᴰ⁾(t) exp(-im ωₕ t) ∈ 𝐂
```

入力:

  * `sol::AbstractDTFTSolution`   | DTFTソリューション構造体 [-]
  * `D::Int`                      | 導関数の次数 [-], デフォルト=0
  * `H::Int`                      | 調和数 [-], デフォルト=1

出力:

  * `ψ::Vector{<:Complex}`        | 非回転動的ファゾール ψₕ⁽ᴰ⁾(t) [?]

```
