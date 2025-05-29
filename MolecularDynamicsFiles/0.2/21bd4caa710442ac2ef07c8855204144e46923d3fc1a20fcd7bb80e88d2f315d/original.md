```julia
ReadTrajectory(
    filepath::String,
    format::MolecularDynamicsFiles.Format.T
) -> MolecularDynamicsFiles.ReadTrajectory

```

Create a ReadTrajectory with trajectory files specified by `filepath`, of format `format`. 

The files are plain text files that may be compressed with gzip.

A trajectory may be contained in a single file with snapshots appended one after another. This is possible only with formats LAMMPS Dump and XYZ.

Alternatively, the trajectory may be defined as a set of files in a directory, with each file containing data for a single snapshot (MDFrame). In this case, files are specified by a file path with the filename containing a mask symbol '*'. A filename with a mask symbol matches all files in that directory with an integer in place of the mask symbol. The timestep for frames is also read from the mask if the timestep is not specified in the files themselves. 

# Arguments:

  * `filepath`: path to trajectory files. Is either a path to a file on disk, or a path with the filename containing a single wildcard "*", representing a mask. A filename with a mask matches all filepaths with an integer (timestep) in place of the mask.
  * `format`: file format of the trajectory (for example Format.LAMMPSDump)
