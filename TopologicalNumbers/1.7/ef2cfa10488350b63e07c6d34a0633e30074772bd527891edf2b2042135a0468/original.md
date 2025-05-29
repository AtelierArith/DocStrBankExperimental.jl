Calculate the winding numbers in the one-dimensional case.

```
calcBerryPhase(Hamiltonian::Function; N::Int=51, gapless::Real=0.0, rounds::Bool=true)
```

Arguments

  * `Hamiltonian::Function`: the Hamiltonian matrix function with one-dimensional wavenumber `k` as an argument.
  * `N::Int`: the number of meshes when discretizing the Brillouin Zone. It is preferable for `N` to be an odd number to increase the accuracy of the calculation.
  * `gapless::Real`: the threshold that determines the state to be degenerate. Coarsening the mesh(`N`) but increasing `gapless` will increase the accuracy of the calculation.
  * `rounds::Bool`: an option to round the value of the topological number to an integer value. The topological number returns a value of type `Int` when `true`, and a value of type `Float` when `false`.

# Definition

The Berry phase of the $n$th band $\nu_{n}$ is defined by

$$
\nu_{n}=\frac{1}{\pi}\sum_{k\in\mathrm{BZ}}U_{n}(k)
$$

The range $\mathrm{BZ}$(Brillouin Zone) is $k\in[0,2\pi]$. $U_{n,i}(k)$ is the link variable at wavenumber $k$. $e_{1}$ is the unit vector.

$$
U_{n}(k)=\braket{\Psi_{n}(k)|\Psi_{n}(k+e_{1})}
$$

$\ket{\Psi_{n}(k)}$ is the wave function of the $n$th band.
