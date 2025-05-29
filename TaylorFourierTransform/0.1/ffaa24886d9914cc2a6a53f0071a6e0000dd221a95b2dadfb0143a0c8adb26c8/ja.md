```
TaylorFourierTransform.frequency(sol::TaylorFourierTransform.AbstractDTFTSolution, H::Int=1)
```

ゼロ次導関数の H次高調波位相の周波数を取得する関数。

```
fₕ(t) = Fₕ + ϕₕ⁽¹⁾(t) / (2 π) ∈ 𝐑⁺
```

参照: [Fast Taylor-Fourier Transform for Monitoring Modern Power Grids with  Real-Time Dynamic Harmonic Estimation](tbp)

入力:

  * `sol::AbstractDTFTSolution`   | DTFT ソリューション構造体 [-]
  * `H::Int`                      | 高調波数 [-], デフォルト=1

出力:

  * `f::Vector{<:Real}`           | 周波数 fₕ(t) [Hz]

```
