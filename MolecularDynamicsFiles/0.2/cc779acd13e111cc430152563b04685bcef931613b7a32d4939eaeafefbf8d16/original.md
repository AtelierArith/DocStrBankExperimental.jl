```julia
WriteTrajectory(
    filepath::String,
    format::MolecularDynamicsFiles.Format.T,
    exported_particle_properties::Vector{Symbol}
) -> MolecularDynamicsFiles.WriteTrajectory

```

Create a WriteTrajectory with trajectory files specified by `filepath`, of format `format`, writing `exported_particle_properties`. 

All the snapshots (MDFrame objects) may be written to a single file, in this case snapshot data will be written one after another in the file.

Alternatively, every frame may be written in a separate file: if the filename of `filepath` contains a single wildcard symbol "*", representing a mask. In this case, every frame is written in a separate file with the timestep of the frame in place of the mask.

If filename of `filepath` ends with ".gz", files are written in GZip format.

`exported_particle_properties` may contain properties defined in the frame,   and also properties:   `:x`, `:y`, `:z`, `:xs`, `:ys`, `:zs`,   `:xu`, `:yu`, `:zu`, `:xsu`, `:ysu`, `:zsu`,   `:ix`, `:iy`, `:iz` if they can be computed from the frame data.   For example, if a frame has unwrapped positions, all of those properties can be computed.  
