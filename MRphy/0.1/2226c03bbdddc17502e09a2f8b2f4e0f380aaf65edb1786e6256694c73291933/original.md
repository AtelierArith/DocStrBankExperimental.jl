```
blochSim!(M, A, B)
```

Hargreave's 𝐴/𝐵, mat/vec, based bloch simulation. Globally or spin-wisely apply matrix `A` and vector `B` over spins, `M`, described in doi:10.1002/mrm.1170

*INPUTS*:

  * `M::TypeND(Real, [2])` (nM, xyz): input spins' magnetizations.
  * `A::TypeND(AbstractFloat,[3])` (nM, 3,3), `A[iM,:,:]` is the `iM`-th 𝐴.
  * `B::TypeND(AbstractFloat,[2])` (nM, 3), `B[iM,:]` is the `iM`-th 𝐵.

*OUTPUTS*:

  * `M::TypeND(Real, [2])` (nM, xyz): spins after applying `B`.
