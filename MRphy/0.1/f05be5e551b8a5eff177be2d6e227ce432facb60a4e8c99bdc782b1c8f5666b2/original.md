```
blochSim!(M, B; T1=(Inf)u"s",T2=(Inf)u"s",γ=γ¹H,dt=(4e-6)u"s",doHist=false)
```

Old school 𝐵-effective magnetic field, `B`, based bloch simulation. Globally or spin-wisely apply `B` over spins, `M`. `M` will be updated by the results.

*INPUTS*:

  * `M::TypeND(Real, [2])` (nM, xyz): input spins' magnetizations.
  * `B::Union{TypeND(B0D, [2,3]), Base.Generator}`: Global, (nT,xyz); Spin-wise, (nM,xyz,nT).

*KEYWORDS*:

  * `T1 & T2 ::TypeND(T0D, [0,1])`: Global, (1,); Spin-wise, (nM,1).
  * `γ::TypeND(Γ0D, [0,1])`: Global, (1,); Spin-wise, (nM, 1). gyro ratio
  * `dt::T0D` (1,), simulation temporal step size, i.e., dwell time.
  * `doHist::Bool`, whether to output spin history through out `B`.

*OUTPUTS*:

  * `M::TypeND(Real, [2])` (nM, xyz): spins after applying `B`.
  * `Mhst::TypeND(Real, [3])` (nM, xyz, nT): spins history during `B`.

See also: [`applyPulse`](@ref), [`blochSim`](@ref).

# Notes:

1. Not much sanity check inside this function, user is responsible for matching up the dimensions.
2. Put relax at the end of each time step may still be inaccurate, since physically spins relax continuously, this noise/nuance may worth study for applications like fingerprinting simulations, etc.
