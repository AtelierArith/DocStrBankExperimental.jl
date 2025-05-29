```
TaylorFourierTransform.signal(sol::TaylorFourierTransform.AbstractDTFTSolution)
```

全体の信号を取得する関数。

```
s(t) = ∑ₕ ξₕ⁽⁰⁾(t) + conj(ξₕ⁽⁰⁾(t)) ∈ 𝐑
```

入力:

  * `sol::AbstractDTFTSolution`   | DTFTソリューション構造体 [-]

出力:

  * `s::Vector{<:Real}`           | 信号 s(t) [?]

```
