```
excitations!(T, tmp, swt::SpinWaveTheory, q)
```

Given a wavevector `q`, solves for the matrix `T` representing quasi-particle excitations, and returns a list of quasi-particle energies. Both `T` and `tmp` must be supplied as $2L×2L$ complex matrices, where $L$ is the number of bands for a single $𝐪$ value.

The columns of `T` are understood to be contracted with the Holstein-Primakoff bosons $[𝐛_𝐪, 𝐛_{-𝐪}^†]$. The first $L$ columns provide the eigenvectors of the quadratic Hamiltonian for the wavevector $𝐪$. The next $L$ columns of `T` describe eigenvectors for $-𝐪$. The return value is a vector with similar grouping: the first $L$ values are energies for $𝐪$, and the next $L$ values are the *negation* of energies for $-𝐪$.

```
excitations!(T, tmp, swt::SpinWaveTheorySpiral, q; branch)
```

Calculations on a [`SpinWaveTheorySpiral`](@ref) additionally require a `branch` index. The possible branches $(1, 2, 3)$ correspond to scattering processes $𝐪 - 𝐤, 𝐪, 𝐪 + 𝐤$ respectively, where $𝐤$ is the ordering wavevector. Each branch will contribute $L$ excitations, where $L$ is the number of spins in the magnetic cell. This yields a total of $3L$ excitations for a given momentum transfer $𝐪$.
