```
excitations(swt::SpinWaveTheory, q)
excitations(swt::SpinWaveTheorySpiral, q; branch)
```

Returns a pair `(energies, T)` providing the excitation energies and eigenvectors. Prefer [`excitations!`](@ref) for performance, which avoids matrix allocations. See the documentation of [`excitations!`](@ref) for more details.
