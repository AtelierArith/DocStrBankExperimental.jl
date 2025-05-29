```
LillyCoefficient([FT=Float64;] smagorinsky=0.16, reduction_factor=1)
```

`Smagorinsky`と一緒に使用すると、[Lilly62](@citet)および[Lilly66](@citet)によって提案された閉じ込めに従ってSmagorinsky係数を計算します。これは、次の形の渦粘性を持ちます。

```
νₑ = (Cˢ * Δᶠ)² * √(2Σ²) * √(1 - Cb * N² / Σ²)
```

ここで、`C²`はSmagorinsky係数、`Δᶠ`はフィルタ幅、`Σ² = ΣᵢⱼΣᵢⱼ`はひずみテンソル`Σᵢⱼ`の二重ドット積、`N²`は全体の浮力勾配、`Cb`は渦粘性に対するリチャードソン数の修正を掛ける定数です。

# 引数

  * `FT`: 浮動小数点型; デフォルトは`Float64`。

# キーワード引数

  * `smagorinsky`: Smagorinsky係数`Cˢ`。デフォルト値はLilly（1966）によって得られた0.16です。
  * `reduction_factor`: Lilly（1962）に基づく浮力項の乗数`Cb`（`reduction_factor = 0`はオフ、`reduction_factor ≠ 0`はオンにします。通常、Lilly（1962）の元の研究によれば、`Cb = 1 / Pr`です。）

# 参考文献

Lilly, D. K. "On the numerical simulation of buoyant convection." Tellus (1962)

Lilly, D. K. "The representation of small-scale turbulence in numerical simulation experiments."     NCAR Manuscript No. 281, 0, (1966)
