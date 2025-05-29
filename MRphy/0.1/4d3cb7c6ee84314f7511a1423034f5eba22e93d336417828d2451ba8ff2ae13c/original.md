```
B2UΦ(B::TypeND(B0D,[2,3]); γ::TypeND(Γ0D,[0,1]), dt::T0D=4e-6u"s")
```

Given 𝐵-effective, `B`, compute rotation axis/angle, `U`/`Φ`.

*INPUTS*:

  * `B::TypeND(B0D, [2,3])` (1,3,nT) or (nM, 3, nT), 𝐵 field.

*KEYWORDS*:

  * `γ::TypeND(Γ0D, [0,1])`: Global, (1,); Spin-wise, (nM, 1). gyro ratio
  * `dt::T0D` (1,), simulation temporal step size, i.e., dwell time.

*OUTPUTS*:

  * `U::TypeND(Real, [2,3])` (1,3,(nT)) or (nM,3,(nT)), axis.
  * `Φ::TypeND(Real, [2,3])` (1,1,(nT)) or (nM,1,(nT)), angle.

See also: [`B2UΦ!`](@ref), [`UΦRot!`](@ref).

# Notes:

Somehow, in-place version, `B2UΦ!(B,U,Φ; γ,dt)`, provokes more allocs in julia.
