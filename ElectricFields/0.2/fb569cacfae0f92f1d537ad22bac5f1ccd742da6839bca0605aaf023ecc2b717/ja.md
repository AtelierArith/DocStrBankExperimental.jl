```
polarization(f)
```

フィールド `f` の偏光の種類を返します。詳細は [`dimensions`](@ref) を参照してください。

# 例

```jldoctest
julia> @field(F) do
           I₀ = 2.0
           T = 2.0
           σ = 3.0
           Tmax = 3.0
       end
線形偏光フィールドで
  - I₀ = 2.0000e+00 au = 7.0188904e16 W cm^-2 =>
    - E₀ = 1.4142e+00 au = 727.2178 GV m^-1
    - A₀ = 0.4502 au
  – 固定キャリア @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV, f = 20.6707 PHz)
  – および持続時間 170.8811 as のガウス包絡線 (強度 FWHM; ±2.00σ)
  – および 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 34.2390 ボーア = 1.8119 nm の帯域幅
  – Uₚ = 0.0507 Ha = 1.3785 eV => α = 0.1433 ボーア = 7.5826 pm

julia> polarization(F)
LinearPolarization()

julia> @field(F) do
           I₀ = 2.0
           T = 2.0
           σ = 3.0
           Tmax = 3.0
           ξ = 1.0
       end
横偏光フィールドで
  - I₀ = 2.0000e+00 au = 7.0188904e16 W cm^-2 =>
    - E₀ = 1.4142e+00 au = 727.2178 GV m^-1
    - A₀ = 0.4502 au
  – ξ = 1.00 (RCP) の楕円キャリア @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV, f = 20.6707 PHz)
  – および持続時間 170.8811 as のガウス包絡線 (強度 FWHM; ±2.00σ)
  – および 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 34.2390 ボーア = 1.8119 nm の帯域幅
  – Uₚ = 0.0507 Ha = 1.3785 eV => α = 0.1433 ボーア = 7.5826 pm

julia> polarization(F)
ArbitraryPolarization()
```
