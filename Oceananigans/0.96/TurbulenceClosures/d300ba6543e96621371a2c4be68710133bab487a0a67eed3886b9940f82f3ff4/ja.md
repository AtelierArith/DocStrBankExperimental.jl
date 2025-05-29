```
RiBasedVerticalDiffusivity([time_discretization = VerticallyImplicitTimeDiscretization(),
                           FT = Float64;]
                           Ri_dependent_tapering = HyperbolicTangentRiDependentTapering(),
                           horizontal_Ri_filter = nothing,
                           minimum_entrainment_buoyancy_gradient = 1e-10,
                           maximum_diffusivity = Inf,
                           maximum_viscosity = Inf,
                           ν₀  = 0.7,
                           κ₀  = 0.5,
                           κᶜᵃ = 1.7,
                           Cᵉⁿ = 0.1,
                           Cᵃᵛ = 0.6,
                           Ri₀ = 0.1,
                           Riᵟ = 0.4,
                           warning = true)
```

"対流調整"係数`ν₀`と`κ₀`から垂直粘度と拡散率を推定するクロージャを返します。これらはリチャードソン数$Ri$の減少関数に掛けられます。

# 引数

  * `time_discretization`: `ExplicitTimeDiscretization()`または`VerticallyImplicitTimeDiscretization()`のいずれかで、                        粘性および拡散フラックスにおける$z$-微分のみを含む項を                        暗黙的な時間離散化で統合します。デフォルトは`VerticallyImplicitTimeDiscretization()`です。
  * `FT`: 浮動小数点型; デフォルトは`Float64`です。

# キーワード引数

  * `Ri_dependent_tapering`: $Ri$依存のテーパリング。オプションは、`PiecewiseLinearRiDependentTapering()`、`HyperbolicTangentRiDependentTapering()`（デフォルト）、および`ExponentialRiDependentTapering()`です。
  * `ν₀`: 非対流粘度（運動粘度の単位、通常はm² s⁻¹）。
  * `κ₀`: トレーサー用の非対流拡散率（拡散率の単位、通常はm² s⁻¹）。
  * `κᶜᵃ`: トレーサー用の対流調整拡散率（拡散率の単位、通常はm² s⁻¹）。
  * `Cᵉⁿ`: トレーサー用の取り込み係数（無次元）。        `Cᵉⁿ = 0`に設定すると、貫通取り込み拡散率がオフになります。
  * `Cᵃᵛ`: 粘度と拡散率の時間平均係数（無次元）。
  * `Ri₀`: 粘度と拡散率が減少する$Ri$の閾値（無次元）。
  * `Riᵟ`: 粘度と拡散率が0に減少する$Ri$幅（無次元）。
  * `minimum_entrainment_buoyancy_gradient`: 取り込み拡散率の適用に対する最小浮力勾配。取り込み浮力勾配が最小値未満の場合、取り込み拡散率は0になります。浮力勾配の単位（通常はs⁻²）。
  * `maximum_diffusivity`: 限界の最大トレーサー拡散率（拡散率の単位、通常はm² s⁻¹）。
  * `maximum_viscosity`: 限界の最大粘度（運動粘度の単位、通常はm² s⁻¹）。
  * `horizontal_Ri_filter`: Riに適用する水平フィルターで、いくつかのシミュレーションのノイズを軽減するのに役立ちます。デフォルトは`nothing`、つまりフィルタリングなしです。もう一つのオプションは`horizontal_Ri_filter = FivePointHorizontalFilter()`です。
