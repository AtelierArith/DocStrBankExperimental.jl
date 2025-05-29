```julia
struct Star2D{P, V, A, M, E, I<:Integer} <: PhysicalParticles.AbstractParticle2D
```

  * `Pos::PhysicalParticles.PVector2D{P} where P`
  * `Vel::PhysicalParticles.PVector2D{V} where V`
  * `Acc::PhysicalParticles.PVector2D{A} where A`
  * `Mass::Any`
  * `ID::Integer`
  * `Collection::PhysicalParticles.Collection`
  * `Ti_endstep::Integer`: タイムライン上の次の整数ステップ。
  * `Ti_begstep::Integer`: タイムライン上の現在の整数ステップ。
  * `GravCost::Integer`: 2粒子間の相互作用ごとに、GravCost += 1
  * `Potential::Any`: 力場における粒子のポテンシャル
  * `OldAcc::Any`: 最後のステップの加速度の正規化を保存します。Tree n-body メソッドで便利です。

AstroSim.jl 用に設計された 2D 粒子タイプ。 [`Collection`](@ref) は `Gadget2` と同様に定義された `Enum` で、インデックスは 1 から始まります。

## 例

```jl
julia> Star2D()
SPHGas 0 GAS: Pos = PVector2D{Float64}(0.0, 0.0), Vel = PVector2D{Float64}(0.0, 0.0), Acc = PVector2D{Float64}(0.0, 0.0), Mass = 0.0, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0, OldAcc = 0.0, Entropy = 0.0, Density = 0.0, Hsml = 0.0, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector2D{Float64}(0.0, 0.0), DivVel = 0.0, CurlVel = 0.0, dHsmlRho = 0.0, Pressure = 0.0, DtEntropy = 0.0, MaxSignalVel = 0.0

julia> Star2D(uAstro, collection = BLACKHOLE)
SPHGas 0 BLACKHOLE: Pos = PVector2D(0.0 kpc, 0.0 kpc), Vel = PVector2D(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1), Acc = PVector2D(0.0 kpc Gyr^-2, 0.0 kpc Gyr^-2), Mass = 0.0 M⊙, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0 kpc^2 M⊙ Gyr^-2, OldAcc = 0.0 kpc Gyr^-2, 
Entropy = 0.0 kpc^2 M⊙ K^-1 Gyr^-2, Density = 0.0 M⊙ kpc^-2, Hsml = 0.0 kpc, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector2D(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1), DivVel = 0.0 Gyr^-1, CurlVel = 0.0 Gyr^-1, dHsmlRho = 0.0 kpc, Pressure = 0.0 M⊙ kpc^-1 Gyr^-2, DtEntropy = 0.0 kpc^2 M⊙ K^-1 Gyr^-3, MaxSignalVel = 0.0 kpc Gyr^-1

julia> Star2D(uSI, id = 1)
SPHGas 1 GAS: Pos = PVector2D(0.0 m, 0.0 m), Vel = PVector2D(0.0 m s^-1, 0.0 m s^-1), Acc = PVector2D(0.0 m s^-2, 0.0 m s^-2), Mass = 0.0 kg, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0 kg m^2 s^-2, OldAcc = 0.0 m s^-2, Entropy = 0.0 kg m^2 K^-1 s^-2, Density = 0.0 kg m^-2, Hsml = 0.0 m, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector2D(0.0 m s^-1, 0.0 m s^-1), DivVel = 0.0 s^-1, CurlVel = 0.0 s^-1, dHsmlRho = 0.0 m, Pressure = 0.0 kg m^-1 s^-2, DtEntropy = 0.0 kg m^2 K^-1 s^-3, MaxSignalVel = 0.0 m s^-1
```
