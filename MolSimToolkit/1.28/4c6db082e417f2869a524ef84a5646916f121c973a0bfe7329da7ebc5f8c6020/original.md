```
distances(simulation, indices1::AbstractVector{<:Integer}, indices2::AbstractVector{<:Integer})
distances(simulation, selection1::AbstractVector{<:PDBTools.Atom}, selection2::AbstractVector{<:PDBTools.Atom})
```

Function that calculates the distance between the centers of mass of two selections in a simulation.

The selections are defined by the indices1 and indices2 vectors, which are the indices of the atoms, or by the selection1 and selection2 vectors, which are vectors of `PDBTools.Atom` objects.

Use `silent=true` to suppress the progress bar.

# Example

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using PDBTools

julia> using MolSimToolkit, MolSimToolkit.Testing

julia> sim = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> ats = atoms(sim);

julia> i1 = findall(sel"protein and residue 1", ats); # indices

julia> i2 = findall(sel"protein and residue 15", ats); # indices

julia> distances(sim, i1, i2; silent=true)
5-element Vector{Float64}:
 23.433267858947584
 30.13791365033211
 28.48617683945202
 27.92740141686934
 23.235012287435566

julia> distances(sim, 
           filter(sel"protein and residue 1", ats), # selection (PDBTools.Atom)
           filter(sel"protein and residue 15", ats); # selection (PDBTools.Atom) 
           silent=true
       )
5-element Vector{Float64}:
 23.433267858947584
 30.13791365033211
 28.48617683945202
 27.92740141686934
 23.235012287435566
```
