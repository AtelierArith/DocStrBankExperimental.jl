```julia
struct Star{P, V, A, M, E, I<:Integer} <: PhysicalParticles.AbstractParticle3D
```

  * `Pos::PhysicalParticles.PVector{P} where P`
  * `Vel::PhysicalParticles.PVector{V} where V`
  * `Acc::PhysicalParticles.PVector{A} where A`
  * `Mass::Any`
  * `ID::Integer`
  * `Collection::PhysicalParticles.Collection`
  * `Ti_endstep::Integer`: Next integer step on the timeline.
  * `Ti_begstep::Integer`: Present integer step on the timeline.
  * `GravCost::Integer`: For each two-particle interaction, GravCost += 1
  * `Potential::Any`: Particle potential in the force field
  * `OldAcc::Any`: Save the normalization of acceleration of last step. Useful in Tree n-body method.

3D Particle type designed for AstroSim.jl.

[`Collection`](@ref) is an `Enum` defined in the same way with `Gadget2`, but start from 1.

## Examples

```jl
julia> Star()
Star 0 GAS: Pos = PVector{Float64}(0.0, 0.0, 0.0), Vel = PVector{Float64}(0.0, 0.0, 0.0), Acc = PVector{Float64}(0.0, 0.0, 0.0), Mass = 0.0, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0, OldAcc = 0.0, Entropy = 0.0, Density = 0.0, Hsml = 0.0, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector{Float64}(0.0, 0.0, 0.0), DivVel = 0.0, CurlVel = 0.0, dHsmlRho = 0.0, Pressure = 0.0, DtEntropy = 0.0, MaxSignalVel = 0.0

julia> Star(uAstro, collection = BLACKHOLE)
Star 0 BLACKHOLE: Pos = PVector(0.0 kpc, 0.0 kpc, 0.0 kpc), Vel = PVector(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1), Acc = PVector(0.0 kpc Gyr^-2, 0.0 kpc Gyr^-2, 0.0 kpc Gyr^-2), Mass = 0.0 M⊙, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0 kpc^2 M⊙ Gyr^-2, OldAcc = 0.0 kpc Gyr^-2, Entropy = 0.0 kpc^2 M⊙ K^-1 Gyr^-2, Density = 0.0 M⊙ kpc^-3, Hsml = 0.0 kpc, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1), DivVel = 0.0 Gyr^-1, CurlVel = 0.0 Gyr^-1, dHsmlRho = 0.0 kpc, Pressure = 0.0 M⊙ kpc^-1 Gyr^-2, DtEntropy = 0.0 kpc^2 M⊙ K^-1 Gyr^-3, MaxSignalVel = 0.0 kpc Gyr^-1

julia> Star(uSI, id = 1)
Star 1 GAS: Pos = PVector(0.0 m, 0.0 m, 0.0 m), Vel = PVector(0.0 m s^-1, 0.0 m s^-1, 0.0 m s^-1), Acc = PVector(0.0 m s^-2, 0.0 m s^-2, 0.0 m s^-2), Mass = 0.0 kg, Ti_endstep = 0, Ti_begstep = 0, Potential = 0.0 kg m^2 s^-2, OldAcc = 0.0 m s^-2, Entropy = 0.0 kg m^2 K^-1 s^-2, Density = 0.0 kg m^-3, Hsml = 0.0 m, Left = 0.0, Right = 0.0, NumNgbFound = 0, RotVel = PVector(0.0 m s^-1, 0.0 m s^-1, 0.0 m s^-1), DivVel = 0.0 s^-1, CurlVel = 0.0 s^-1, dHsmlRho = 0.0 m, Pressure = 0.0 kg m^-1 s^-2, DtEntropy = 0.0 
kg m^2 K^-1 s^-3, MaxSignalVel = 0.0 m s^-1
```
