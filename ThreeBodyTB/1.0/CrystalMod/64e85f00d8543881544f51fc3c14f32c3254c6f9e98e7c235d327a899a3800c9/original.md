```
mutable struct crystal{T}
```

Holds basic crystal structure information, type T. Use `makecrys` to easily construct.

Note: you can create supercells like

```julia-repl
julia> c = makecrys([5.0 0 0; 0 5.0 0; 0 0 5.0], [0.0 0.0 0.0], ["H"])
A1=     5.00000  0.00000  0.00000
A2=     0.00000  5.00000  0.00000
A3=     0.00000  0.00000  5.00000

H    0.00000  0.00000  0.00000


julia> c*[2,2,2]
A1=     10.00000  0.00000  0.00000
A2=     0.00000  10.00000  0.00000
A3=     0.00000  0.00000  10.00000

H    0.00000  0.00000  0.00000
H    0.00000  0.00000  0.50000
H    0.00000  0.50000  0.00000
H    0.00000  0.50000  0.50000
H    0.50000  0.00000  0.00000
H    0.50000  0.00000  0.50000
H    0.50000  0.50000  0.00000
H    0.50000  0.50000  0.50000
```

# Holds

  * `A::Array{T,2}` 3 × 3 lattice vectors, Bohr (atomic units) internally.
  * `coords::Array{T,2}` num_atoms × 3  atomic positions, fractional units.
  * `types::Array{String,1}` atomic names, like `"H"` or `"Zn"`.
  * `types::Array{Symbol,1}` atomic names, but julia Symbols like `:H` or `:Zn`, for nominally faster internal evaluation.
  * `nat::Int64` number of atoms.
