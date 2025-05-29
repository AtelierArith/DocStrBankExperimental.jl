```
TaylorFourierTransform.phasor(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

H次の動的ファゾールのD次導関数を取得する関数。ゼロ次の動的ファゾールの場合、動的ファゾールの実部のみが返されます。

```
∀ h ∈ {0}:
    ξ₀⁽ᴰ⁾(t) ∈ ℝ
∀ h ∉ {0}:
    ξₕ⁽ᴰ⁾(t) ∈ ℂ
```

入力:

  * `sol::AbstractDTFTSolution`   | DTFTソリューション構造体 [-]
  * `D::Int`                      | 導関数の次数 [-], デフォルト=0
  * `H::Int`                      | ハーモニック番号 [-], デフォルト=1

出力:

  * `ξ::Vector{<:Complex}`        | 動的ファゾール ξₕ⁽ᴰ⁾(t) [?]

```
