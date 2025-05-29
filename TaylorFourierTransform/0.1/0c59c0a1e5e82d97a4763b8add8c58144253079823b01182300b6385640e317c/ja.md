```
TaylorFourierTransform.rocof(sol::TaylorFourierTransform.AbstractDTFTSolution, H::Int=1)
```

ゼロ次導関数のH次高調波位相の周波数変化率を取得する関数。

```
rₕ(t) = ϕₕ⁽²⁾(t) / (2 π)² ∈ 𝐑
```

参照: [Fast Taylor-Fourier Transform for Monitoring Modern Power Grids with  Real-Time Dynamic Harmonic Estimation](tbp)

入力:

  * `sol::AbstractDTFTSolution`   | DTFTソリューション構造体 [-]
  * `H::Int`                      | 高調波数 [-], デフォルト=1

出力:

  * `r::Vector{<:Real}`           | rocof rₕ(t) [Hz²]

```
