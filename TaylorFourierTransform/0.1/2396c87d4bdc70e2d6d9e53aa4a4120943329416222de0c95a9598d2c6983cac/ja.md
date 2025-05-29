```
TaylorFourierTransform.signal(sol::TaylorFourierTransform.AbstractDTFTSolution, H::Int)
```

H次ハーモニック信号を取得する関数。

```
∀ h ∈ {0}:
    s₀(t) = ξ₀⁽⁰⁾(t) ∈ 𝐑
∀ h ∉ {0}: 
    sₕ(t) = ℜ[ξₕ⁽⁰⁾(t) + conj(ξₕ⁽⁰⁾(t))] ∈ 𝐑
```

注: 本質的に、実数演算子 `ℜ[]` は不要ですが、複素数 `x + j0` を実数 `x` に変換するために使用されます。

入力:

  * `sol::AbstractDTFTSolution`   | DTFTソリューション構造体 [-]
  * `H::Int`                      | ハーモニック番号 [-]

出力:

  * `s::Vector{<:Real}`           | 信号 sₕ(t) [?]

```
