```
SmagorinskyLilly([time_discretization::TD = ExplicitTimeDiscretization(), FT=Float64;] C=0.16, Cb=1.0, Pr=1.0)
```

`[Lilly62](@citet)`, `[Smagorinsky1958](@citet)`, `[Smagorinsky1963](@citet)`, および `[Lilly66](@citet)` によって提案された乱流閉じ込めに関連する `SmagorinskyLilly` 型を返します。この型は、次の形の渦粘性を持ちます。

```
νₑ = (Cˢ * Δᶠ)² * √(2Σ²) * √(1 - Cb * N² / Σ²)
```

および次の形の渦拡散率を持ちます。

```
κₑ = νₑ / Pr
```

ここで `Δᶠ` はフィルタ幅、`Σ² = ΣᵢⱼΣᵢⱼ` はひずみテンソル `Σᵢⱼ` の二重ドット積、`Pr` は乱流プラントル数、`N²` は全浮力勾配、`Cb` は渦粘性へのリチャードソン数修正を掛ける定数です。

# 引数

  * `time_discretization`: `ExplicitTimeDiscretization()` または `VerticallyImplicitTimeDiscretization()` のいずれかで、                        粘性および拡散フラックスにおける $z$-微分のみを含む項を                        暗黙的な時間離散化で統合します。                        デフォルトは `ExplicitTimeDiscretization()` です。
  * `FT`: 浮動小数点型; デフォルトは `Float64` です。

# キーワード引数

  * `Cˢ`: スマゴリンシー係数。デフォルト値は 0.16 で、Lilly (1966) によって得られました。
  * `Cb`: Lilly (1962) に基づく浮力項の乗数 (`Cb = 0` はオフ、`Cb ≠ 0` はオンにします。       通常、Lilly (1962) の元の研究によれば、`Cb = 1 / Pr` です。)
  * `Pr`: 各トレーサーの乱流プラントル数。すべてのトレーサーに適用される定数、または各トレーサー個別のフィールドを持つ `NamedTuple`。

# 参考文献

Smagorinsky, J. "On the numerical integration of the primitive equations of motion for     baroclinic flow in a closed region." Monthly Weather Review (1958)

Lilly, D. K. "On the numerical simulation of buoyant convection." Tellus (1962)

Smagorinsky, J. "General circulation experiments with the primitive equations: I.     The basic experiment." Monthly Weather Review (1963)

Lilly, D. K. "The representation of small-scale turbulence in numerical simulation experiments."     NCAR Manuscript No. 281, 0, (1966)
