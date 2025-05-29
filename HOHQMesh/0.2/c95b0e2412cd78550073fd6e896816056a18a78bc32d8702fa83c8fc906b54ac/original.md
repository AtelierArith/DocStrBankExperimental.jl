```
generate_mesh(control_file;
              output_directory="out",
              mesh_filename=nothing, plot_filename=nothing, stats_filename=nothing,
              verbose=false, subdivision_maximum=8)
```

Generate a mesh based on the `control_file` with the HOHQMesh mesh generator and store resulting files in `output_directory`.

You can set the mesh filename, the plot filename, and the statistics filename using the keyword arguments `mesh_filename`, `plot_filename`, and `stats_filename`, respectively. If set to `nothing`, the filenames for the mesh file, plot file, and statistics file are generated automatically from the control file name. For example, `path/to/ControlFile.control` will result in output files `ControlFile.mesh`, `ControlFile.tec`, and `ControlFile.txt`.

You can activate verbose output from HOHQMesh that prints additional messages and debugging mesh information with the keyword argument `verbose`.

To override the maximum number of allowable subdivisions in the quad tree during meshing adjust the value of `subdivision_maximum`. The default value of `subdivision_maximum` is 8, meaning that elements can be up to a factor of `2^8` smaller than the background grid. Note, think before doing this! It could be adjusting the boundary curves, background grid size, adding local refinement regions, or some combination may remove the need to adjust the subdivision depth.

This function returns the output to `stdout` of the HOHQMesh binary when generating the mesh.
