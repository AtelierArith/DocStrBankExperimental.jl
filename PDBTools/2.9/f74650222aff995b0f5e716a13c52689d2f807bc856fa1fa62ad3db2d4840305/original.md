```
write_pdb(filename::String, atoms::AbstractVector{<:Atom}, [selection]; header=:auto, footer=:auto, append=false)
```

Write a PDB file with the atoms in `atoms` to `filename`. The `selection` argument is a string that can be used to select a subset of the atoms in `atoms`. For example, `write_pdb("test.pdb", atoms, "name CA")`.

# Arguments

  * `filename::String`: The name of the file to write.
  * `atoms::AbstractVector{<:Atom}`: The atoms to write to the file.

# Optional positional argument

  * `selection::String`: A selection string to select a subset of the atoms in `atoms`.

# Keyword arguments

  * `header::Union{String, Nothing}=:auto`: The header to add to the PDB file. If `:auto`, a header will be added with the number of atoms in `atoms`.
  * `footer::Union{String, Nothing}=:auto`: The footer to add to the PDB file. If `:auto`, a footer will be added with the "END" keyword.
  * `append::Bool=false`: If `true`, the atoms will be appended to the file instead of overwriting it.

!!! compat
    The `append` keyword argument is available in PDBTools.jl v2.7.0 and later.

