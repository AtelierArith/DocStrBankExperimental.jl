```julia
read_w90_tbdat(filename)

```

Read `prefix_tb.dat`.

# Return

  * `lattice`: each column is a lattice vector in Å
  * `Rvectors`: $\mathbf{R}$-vectors on which operators are defined
  * `Rdegens`: degeneracies of each $\mathbf{R}$-vector
  * `H`: Hamiltonian $\mathbf{H}(\mathbf{R})$
  * `r_x`: $x$-component of position operator
  * `r_x`: $y$-component of position operator
  * `r_x`: $z$-component of position operator
  * `header`: the first line of the file
