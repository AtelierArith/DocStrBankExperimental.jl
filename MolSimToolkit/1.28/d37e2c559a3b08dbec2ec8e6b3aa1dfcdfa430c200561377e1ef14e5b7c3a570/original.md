```
center_of_mass(
    indices::AbstractVector{Int};
    simulation::Simulation,
    positions::FramePositions,
    iref::Union{Nothing,Int} = max(1, div(length(indices),2)),
)
```

Calculate the center of mass of a selection of atoms in a simulation given the positions. The selection is defined by the `indices` vector, which is the indices of the atoms.

The `iref` parameter is the index of the reference atom. The center of mass is calculated by first computing the minimum-image of all atoms relative to this atom. By default, it is the atom closest to the middle of the indices vector. If `iref` is `nothing`, the center of mass is calculated without wrapping the coordinates.

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using PDBTools 

julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> protein_indices = findall(sel"protein", atoms(simulation));

julia> first_frame!(simulation); # move simulation to the first frame

julia> coor = positions(current_frame(simulation));

julia> cm = center_of_mass(protein_indices, simulation, coor)
3-element Point3D{Float64} with indices SOneTo(3):
 -3.7290442807974906
 -1.5339226637687564
  1.960640754560446
```

!!! compat
    The `iref=nothing` option was added in version 1.22.0.

