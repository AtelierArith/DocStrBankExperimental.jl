```
most_representative_structure(simulation::Simulation; atoms = nothing)
```

Find the most representative structure in a simulation.  The most representative structure is the one that minimizes the RMSD with respect to the average structure of the simulation.  The average structure is defined iteratively, first by aligning all frames to the first frame, and then by averaging the aligned structures. The structure most similar to the average is then identified and used as the reference structure for the next iteration. The process is repeated until the structure most similar to the average is the same as the previous iteration.

# Arguments

  * `simulation::Simulation`: Simulation object.
  * `atoms`: Atoms to consider in the calculation:

      * `atoms` is `nothing`: the function will consider all alpha-carbons in proteins (`"protein and name CA"`).
      * `atoms` is an `AbstractVector{<:PDBTools.Atom}`: the function will consider the atoms in the vector.
      * `atoms` is an `AbstractVector{<:Int}`: the function will consider the atoms with the indices in the vector.
      * `atoms` is a `String`: the function will consider the atoms selected by the string.

# Returns

  * Tuple `(Int, Float64)`, with:

      * Index of the most representative structure.
      * RMSD of the most representative structure with respect to the average structure.

# Example

```julia-repl
julia> using MolSimToolkit, MolSimToolkit.Testing, PDBTools

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> most_representative_structure(simulation) # atoms == nothing (all alpha-carbons in proteins)
(4, 1.1681526249035976)

julia> most_representative_structure(simulation; atoms = "protein and name CA") # atoms is a String
(4, 1.1681526249035976)

julia> calphas = select(atoms(simulation), "name CA");

julia> most_representative_structure(simulation; atoms = calphas) # atoms is an Vector{PDBTools.Atom}
(4, 1.1681526249035976)

julia> ica = PDBTools.index.(calphas)

julia> most_representative_structure(simulation; atoms = ica) # atoms is an vector of indices
(4, 1.1681526249035976)
```
