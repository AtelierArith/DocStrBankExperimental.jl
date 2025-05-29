```
Cell
```

Data type for cell.

# Fields

  * `name::String`: stores the name of the cell.
  * `lattice::Lattice{<:Real}`: stores metadata about the lattice
  * `atoms::Array{Atom{<:Real}, 1}`: stroes metadata of all atoms in the cell
  * `numbers::Array{<:Integer, 1}`: stroes the numbers of atoms of elements
  * `symbols::Array{String, 1}`: stores the chemical symbols of atoms of elements
