```
intensities(swt::SpinWaveTheory, qpts; energies, kernel, kT=0)
intensities(sc::SampledCorrelations, qpts; energies, kernel=nothing, kT)
```

Calculates dynamical pair correlation intensities for a set of $𝐪$-points in reciprocal space.

Linear spin wave theory calculations are performed with an instance of [`SpinWaveTheory`](@ref). The alternative [`SpinWaveTheorySpiral`](@ref) allows to study generalized spiral orders with a single, incommensurate-$𝐤$ ordering wavevector. Another alternative [`SpinWaveTheoryKPM`](@ref) is favorable for calculations on large magnetic cells, and allows to study systems with disorder. An optional nonzero temperature `kT` will scale intensities by the quantum thermal occupation factor $|1 + n_B(ω)|$ where $n_B(ω) = 1/(e^{βω}-1)$ is the Bose function.

Intensities can also be calculated for `SampledCorrelations` associated with classical spin dynamics. In this case, thermal broadening will already be present, and the line-broadening `kernel` becomes optional. Conversely, the parameter `kT` becomes required. If positive, it will introduce an intensity correction factor $|βω (1 + n_B(ω))|$ that undoes the occupation factor for the classical Boltzmann distribution and applies the quantum thermal occupation factor. The special choice `kT = nothing` will suppress the classical-to-quantum correction factor, and yield statistics consistent with the classical Boltzmann distribution.
