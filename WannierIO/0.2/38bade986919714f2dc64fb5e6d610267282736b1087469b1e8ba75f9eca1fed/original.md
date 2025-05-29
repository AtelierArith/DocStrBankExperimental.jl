```julia
read_w90_hrdat(filename)

```

Read `prefix_hr.dat`.

# Return

  * `Rvectors`: $\mathbf{R}$-vectors on which operators are defined
  * `Rdegens`: degeneracies of each $\mathbf{R}$-vector
  * `H`: Hamiltonian $\mathbf{H}(\mathbf{R})$
  * `header`: the first line of the file
