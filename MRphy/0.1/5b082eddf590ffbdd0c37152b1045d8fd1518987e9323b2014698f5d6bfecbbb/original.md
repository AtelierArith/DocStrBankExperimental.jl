```
B2AB(B; T1=(Inf)u"s", T2=(Inf)u"s", γ=γ¹H, dt=(4e-6)u"s")
```

Turn B-effective into Hargreave's 𝐴/𝐵, mat/vec, see: doi:10.1002/mrm.1170.

*INPUTS*:

  * `B::Union{TypeND(B0D, [2,3]), Base.Generator}`: Global, (nT,xyz); Spin-wise, (nM,xyz,nT).

*KEYWORDS*:

  * `T1 & T2 ::TypeND(T0D, [0,1])`: Global, (1,); Spin-wise, (nM,1).
  * `γ::TypeND(Γ0D, [0,1])`: Global, (1,); Spin-wise, (nM, 1). gyro ratio
  * `dt::T0D` (1,), simulation temporal step size, i.e., dwell time.

*OUTPUTS*:

  * `A::TypeND(AbstractFloat,[3])` (nM, 3,3), `A[iM,:,:]` is the `iM`-th 𝐴.
  * `B::TypeND(AbstractFloat,[2])` (nM, 3), `B[iM,:]` is the `iM`-th 𝐵.

See also: [`rfgr2B`](@ref), [`Pulse2B`](@ref).
