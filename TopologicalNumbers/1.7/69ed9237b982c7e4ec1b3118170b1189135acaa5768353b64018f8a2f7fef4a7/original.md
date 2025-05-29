Calculate the first Chern numbers in the two-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern](@cite).

```
calcChern(Hamiltonian::Function; N::Int=51, gapless::Real=0.0, rounds::Bool=true)
```

Arguments

  * Hamiltionian::Function: The Hamiltonian matrix with two-dimensional wavenumber `k` as an argument.
  * N::Int=51: The number of meshes when discretizing the Brillouin Zone. It is preferable for `N` to be an odd number to increase the accuracy of the calculation.
  * gapless::Real: The threshold that determines the state to be degenerate. Coarsening the mesh(`N`) but increasing `gapless` will increase the accuracy of the calculation.
  * rounds::Bool=true: An option to round the value of the topological number to an integer value. The topological number returns a value of type `Int` when `true`, and a value of type `Float` when `false`.

# Definition

The first Chern number of the $n$th band $\nu_{n}$ is defined by

$$
\nu_{n}=\frac{1}{2\pi}\sum_{\bm{k}\in\mathrm{BZ}}\mathrm{Im}\left[\mathrm{Log}\left[U_{n,1}(\bm{k})U_{n,2}(\bm{k}+\bm{e}_{1})U_{n,1}^{*}(\bm{k}+\bm{e}_{2})U_{n,2}^{*}(\bm{k})\right]\right]
$$

The range $\mathrm{BZ}$(Brillouin Zone) is $\bm{k}\in[0,2\pi]^{2}$. $U_{n,i}(\bm{k})$ is the link variable at wavenumber $\bm{k}$. $\bm{e}_{i}$ is the unit vector.

$$
U_{n,i}(\bm{k})=\braket{\Psi_{n}(\bm{k})|\Psi_{n}(\bm{k}+\bm{e}_{i})}
$$

$\ket{\Psi_{n}(\bm{k})}$ is the wave function of the $n$th band.
