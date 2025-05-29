Calculate the Berry flux in the two-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern](@cite).

```
calcBerryFlux(Hamiltonian::Function, n::Vector{Int64}; N::Int=51, gapless::Real=0.0, rounds::Bool=true)
```

Arguments

  * Hamiltionian::Function: the Hamiltonian matrix with one-dimensional wavenumber `k` as an argument.
  * n::Vector{Int64}: The wavenumber($2\pi n/N$) when calculating Berry flux.
  * N::Int=51: The number of meshes when discretizing the Brillouin Zone. It is preferable for `N` to be an odd number to increase the accuracy of the calculation.
  * gapless::Real: The threshold that determines the state to be degenerate. Coarsening the mesh(`N`) but increasing `gapless` will increase the accuracy of the calculation.
  * rounds::Bool=true: An option to round the value of the topological number to an integer value. The topological number returns a value of type `Int` when `true`, and a value of type `Float` when `false`.

# Definition

The Berry flux at the wavenumber $\bm{k}$ of the $n$th band $F_{n}(\bm{k})$ is defined by

$$
F_{n}(\bm{k})=f_{n}(\bm{k})-df_{n}(\bm{k})
$$

$$
f_{n}(\bm{k})=\frac{1}{2\pi}\mathrm{Im}\left[\mathrm{Log}\left[U_{n,1}(\bm{k})U_{n,2}(\bm{k}+\bm{e}_{1})U_{n,1}^{*}(\bm{k}+\bm{e}_{2})U_{n,1}^{*}(\bm{k})\right]\right]
$$

$$
df_{n}(\bm{k})=\frac{1}{2\pi}\mathrm{Im}\left[\mathrm{Log}[U_{n,1}(\bm{k})]+\mathrm{Log}[U_{n,2}(\bm{k}+\bm{e}_{1})]-\mathrm{Log}[U_{n,1}(\bm{k}+\bm{e}_{2})]-\mathrm{Log}[U_{n,1}(\bm{k})]\right]
$$

$U_{n,i}(\bm{k})$ is the link variable at wavenumber $\bm{k}$. $\bm{e}_{i}$ is the unit vector.

$$
U_{n,i}(\bm{k})=\braket{\Psi_{n}(\bm{k})|\Psi_{n}(\bm{k}+\bm{e}_{i})}
$$

$\ket{\Psi_{n}(\bm{k})}$ is the wave function of the $n$th band.
