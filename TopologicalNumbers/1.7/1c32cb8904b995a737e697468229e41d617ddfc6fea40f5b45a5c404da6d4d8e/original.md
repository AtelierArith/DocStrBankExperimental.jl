Calculate the Weyl node in the three-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern](@cite).

```
calcWeylNode(Hamiltonian::Function, n::Vector{Int64}; N::Int=51, gapless::Real=0.0, rounds::Bool=true)
```

Arguments

  * Hamiltionian::Function: the Hamiltonian matrix with three-dimensional wavenumber `k` as an argument.
  * n::Vector{Int64}: The wavenumber($2\pi\bm{n}/N$) when calculating Weyl node.
  * N::Int=51: The number of meshes when discretizing the Brillouin Zone. It is preferable for `N` to be an odd number to increase the accuracy of the calculation.
  * gapless::Real: The threshold that determines the state to be degenerate. Coarsening the mesh(`N`) but increasing `gapless` will increase the accuracy of the calculation.
  * rounds::Bool=true: An option to round the value of the topological number to an integer value. The topological number returns a value of type `Int` when `true`, and a value of type `Float` when `false`.
