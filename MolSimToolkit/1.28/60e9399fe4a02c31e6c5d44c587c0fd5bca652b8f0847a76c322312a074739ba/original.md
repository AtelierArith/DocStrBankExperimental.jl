```
rmsd(simulation::Simulation, indices::AbstractVector{<:Integer}; mass = nothing, reference_frame = nothing, show_progress = true)
```

Computes the root mean square deviation (RMSD) between two sets of points in along a trajectory.

# Arguments

  * `indices` vector contains the indices of the atoms to be considered.
  * `mass` argument can be used to provide the mass of the atoms if they are not the same.
  * `reference_frame` argument can be used to provide a reference frame to align the trajectory to:

      * If `reference_frame == nothing`, the first frame will be used (default behavior).
      * If `reference_frame == :average`, the average structure will be used.
      * If `reference_frame` is an integer, the frame at that index will be used as reference.

# Examples

## Computing the rmsd along a trajectory

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> using PDBTools

julia> atoms = readPDB(Testing.namd_pdb);

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> cas = findall(sel"name CA", atoms); # CA indices

julia> rmsd(simulation, cas; show_progress=false)
5-element Vector{Float64}:
 0.0
 2.8388710154609034
 2.9776998440690385
 2.4621444212469483
 3.8035683196100796

julia> rmsd(simulation, cas; reference_frame=:average, show_progress=false)
5-element Vector{Float64}:
 1.8995986972454748
 2.1512244220536973
 1.5081703191869376
 1.1651111324544219
 2.757039151265317
```
