```
  PaddedField(field, a, b)
```

任意の電場 `field` のラッパーで、通常の [`span`](@ref) の前に `a` 単位の時間、後に `b` 単位の時間をパディングします。

# 例

```jldoctest
julia> @field(A) do
           I₀ = 1.0
           T = 2.0
           σ = 3.0
           Tmax = 3.0
       end
線形偏光場で
  - I₀ = 1.0000e+00 au = 3.5094452e16 W cm^-2 =>
    - E₀ = 1.0000e+00 au = 514.2207 GV m^-1
    - A₀ = 0.3183 au
  – 固定キャリア @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV, f = 20.6707 PHz)
  – 170.8811 as の持続時間のガウス包絡線 (強度 FWHM; ±2.00σ)
  – 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 34.2390 ボーhr = 1.8119 nm の帯域幅
  – Uₚ = 0.0253 Ha = 689.2724 meV => α = 0.1013 ボーhr = 5.3617 pm

julia> B = PaddedField(A, 10.0, 30.0)
10.0000 ジフィの前のパディング = 241.8884 as および 30.0000 ジフィの後のパディング = 725.6653 as の
線形偏光場で
  - I₀ = 1.0000e+00 au = 3.5094452e16 W cm^-2 =>
    - E₀ = 1.0000e+00 au = 514.2207 GV m^-1
    - A₀ = 0.3183 au
  – 固定キャリア @ λ = 14.5033 nm (T = 48.3777 as, ω = 3.1416 Ha = 85.4871 eV, f = 20.6707 PHz)
  – 170.8811 as の持続時間のガウス包絡線 (強度 FWHM; ±2.00σ)
  – 0.3925 Ha = 10.6797 eV ⟺ 2.5823 PHz ⟺ 34.2390 ボーhr = 1.8119 nm の帯域幅
  – Uₚ = 0.0253 Ha = 689.2724 meV => α = 0.1013 ボーhr = 5.3617 pm

julia> span(A), span(B)
(-6.0 .. 6.0, -16.0 .. 36.0)
```
