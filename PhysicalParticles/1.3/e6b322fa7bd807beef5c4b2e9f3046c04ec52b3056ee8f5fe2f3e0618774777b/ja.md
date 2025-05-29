```julia
struct Star{P, V, A, M, E, I<:Integer} <: PhysicalParticles.AbstractParticle3D
```

  * `Pos::PhysicalParticles.PVector{P} where P`
  * `Vel::PhysicalParticles.PVector{V} where V`
  * `Acc::PhysicalParticles.PVector{A} where A`
  * `Mass::Any`
  * `ID::Integer`
  * `Collection::PhysicalParticles.Collection`
  * `Ti_endstep::Integer`: 次のタイムラインの整数ステップ。
  * `Ti_begstep::Integer`: 現在のタイムラインの整数ステップ。
  * `GravCost::Integer`: 2粒子間の相互作用ごとに、GravCost += 1
  * `Potential::Any`: 力場における粒子のポテンシャル
  * `OldAcc::Any`: 最後のステップの加速度の正規化を保存します。Tree n-body メソッドで便利です。

AstroSim.jl 用に設計された 3D 粒子タイプ。

[`Collection`](@ref) は `Gadget2` と同様に定義された `Enum` ですが、1 から始まります。

## 例

```jl
julia> Star()
Star 0 GAS: Pos = PVector{Float64}(0.0, 0.0, 0.0), Vel = PVector{Float64}(0.0, 0.0, 0.0), Acc = PVector{Float64}(0.0, 0.0, 0.0), Mass = 0.0, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0, OldAcc = 0.0, Entropy = 0.0, Density = 0.0, Hsml = 0.0, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector{Float64}(0.0, 0.0, 0.0), DivVel = 0.0, CurlVel = 0.0, dHsmlRho = 0.0, Pressure = 0.0, DtEntropy = 0.0, MaxSignalVel = 0.0

julia> Star(uAstro, collection = BLACKHOLE)
Star 0 BLACKHOLE: Pos = PVector(0.0 kpc, 0.0 kpc, 0.0 kpc), Vel = PVector(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1), Acc = PVector(0.0 kpc Gyr^-2, 0.0 kpc Gyr^-2, 0.0 kpc Gyr^-2), Mass = 0.0 M⊙, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0 kpc^2 M⊙ Gyr^-2, OldAcc = 0.0 kpc Gyr^-2, Entropy = 0.0 kpc^2 M⊙ K^-1 Gyr^-2, Density = 0.0 M⊙ kpc^-3, Hsml = 0.0 kpc, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1), DivVel = 0.0 Gyr^-1, CurlVel = 0.0 Gyr^-1, dHsmlRho = 0.0 kpc, Pressure = 0.0 M⊙ kpc^-1 Gyr^-2, DtEntropy = 0.0 kpc^2 M⊙ K^-1 Gyr^-3, MaxSignalVel = 0.0 kpc Gyr^-1

julia> Star(uSI, id = 1)
Star 1 GAS: Pos = PVector(0.0 m, 0.0 m, 0.0 m), Vel = PVector(0.0 m s^-1, 0.0 m s^-1, 0.0 m s^-1), Acc = PVector(0.0 m s^-2, 0.0 m s^-2, 0.0 m s^-2), Mass = 0.0 kg, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0 kg m^2 s^-2, OldAcc = 0.0 m s^-2, Entropy = 0.0 kg m^2 K^-1 s^-2, Density = 0.0 kg m^-3, Hsml = 0.0 m, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector(0.0 m s^-1, 0.0 m s^-1, 0.0 m s^-1), DivVel = 0.0 s^-1, CurlVel = 0.0 s^-1, dHsmlRho = 0.0 m, Pressure = 0.0 kg m^-1 s^-2, DtEntropy = 0.0 
kg m^2 K^-1 s^-3, MaxSignalVel = 0.0 m s^-1
```
