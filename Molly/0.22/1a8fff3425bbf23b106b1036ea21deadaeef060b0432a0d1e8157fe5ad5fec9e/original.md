```
System(coordinate_file, force_field; <keyword arguments>)
```

Read a coordinate file in a file format readable by Chemfiles and apply a force field to it.

Atom names should exactly match residue templates - no searching of residue templates is carried out.

```
System(coordinate_file, topology_file; <keyword arguments>)
System(T, coordinate_file, topology_file; <keyword arguments>)
```

Read a Gromacs coordinate file and a Gromacs topology file with all includes collapsed into one file.

Gromacs file reading should be considered experimental. The `implicit_solvent`, `kappa` and `rename_terminal_res` keyword arguments are not available when reading Gromacs files.

# Arguments

  * `boundary=nothing`: the bounding box used for simulation, read from the   file by default.
  * `velocities=nothing`: the velocities of the atoms in the system, set to   zero by default.
  * `loggers=()`: the loggers that record properties of interest during a   simulation.
  * `units::Bool=true`: whether to use Unitful quantities.
  * `array_type=Array`: the array type for the simulation, for example   use `CuArray` or `ROCArray` for GPU support.
  * `dist_cutoff=1.0u"nm"`: cutoff distance for long-range interactions.
  * `dist_neighbors=1.2u"nm"`: cutoff distance for the neighbor list, should not   be less than `dist_cutoff`. Not relevant if [`GPUNeighborFinder`](@ref) is   used since the neighbors are calculated each step.
  * `center_coords::Bool=true`: whether to center the coordinates in the   simulation box.
  * `neighbor_finder_type`: which neighbor finder to use, default is   [`CellListMapNeighborFinder`](@ref) on CPU, [`GPUNeighborFinder`](@ref)   on CUDA compatible GPUs and [`DistanceNeighborFinder`](@ref) on non-CUDA   compatible GPUs.
  * `data=nothing`: arbitrary data associated with the system.
  * `implicit_solvent=nothing`: specify a string to add an implicit solvent   model, options are "obc1", "obc2" and "gbn2".
  * `kappa=0.0u"nm^-1"`: the kappa value for the implicit solvent model if one   is used.
  * `rename_terminal_res=true`: whether to rename the first and last residues   to match the appropriate atom templates, for example the first (N-terminal)   residue could be changed from "MET" to "NMET".
