```
rmsd_matrix(
    simulation::Simulation, 
    indices::AbstractVector{<:Integer}; 
    mass::Union{AbstractVector{<:Integer}, Nothing} = nothing,
    align::Bool = true,
    show_progress = true,
)
```

Computes the RMSD matrix for a set of atoms along a trajectory.

The `indices` vector contains the indices of the atoms to be considered.  The `mass` argument can be used to provide the mass of the atoms if they are not the same. The `align` argument can be used to align the frames before computing the RMSD.

The `show_progress` argument can be used to show a progress bar.

# Returns

A symetric matrix with the RMSD values between each pair of frames. For example, in  a trajectory with 5 frames, the matrix will be a 5x5 matrix with the RMSD values between the structures of each pair of frames.

# Example

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> using PDBTools

julia> atoms = readPDB(Testing.namd_pdb);

julia> cas = findall(Select("name CA"), atoms); # CA indices

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> rmsd_matrix(simulation, cas; show_progress=false)
5×5 Matrix{Float64}:
 0.0      2.83887  2.9777   2.46214  3.80357
 2.83887  0.0      2.35492  2.64463  4.68028
 2.9777   2.35492  0.0      2.08246  3.46149
 2.46214  2.64463  2.08246  0.0      2.97835
 3.80357  4.68028  3.46149  2.97835  0.0
```
