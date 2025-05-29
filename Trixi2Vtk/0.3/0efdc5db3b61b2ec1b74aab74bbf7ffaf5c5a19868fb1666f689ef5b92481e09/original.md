```
trixi2vtk(filename::AbstractString...;
          format=:vtu, verbose=false, hide_progress=false, pvd=nothing,
          output_directory=".", nvisnodes=nothing, save_celldata=true,
          reinterpolate=true, data_is_uniform=false)
```

Convert Trixi-generated output files to VTK files (VTU or VTI).

# Arguments

  * `filename`: One or more Trixi solution/restart/mesh files to convert to a VTK file.             Filenames support file globbing, e.g., "solution*" to match all files starting             with `solution`.
  * `format`: Output format for solution/restart files. Can be 'vtu' or 'vti'.
  * `verbose`: Set to `true` to enable verbose output.
  * `hide_progress`: Hide progress bar (will be hidden automatically if `verbose` is `true`).
  * `pvd`: Use this filename to store PVD file (instead of auto-detecting name). Note that        only the name will be used (directory and file extension are ignored).
  * `output_directory`: Output directory where generated files are stored.
  * `nvisnodes`: Number of visualization nodes per element.              (default: number of DG nodes for StructuredMesh or UnstructuredMesh2D,                        twice the number of DG nodes for TreeMesh).              A value of `0` (zero) uses the number of nodes in the DG elements.
  * `save_celldata`: Boolean value to determine if cell-based data should be saved.                  (default: `true`)
  * `reinterpolate`: Boolean value to determine if data should be reinterpolated                  onto uniform points. When `false` the raw data at the compute nodes                  is copied into the appropriate format.                  (default: `true`)
  * `data_is_uniform`: Boolean to indicate if the data to be converted is from a finite difference                    method on a uniform grid of points.                    (default: `false`)

# Examples

```julia
julia> trixi2vtk("out/solution_000*.h5")
[...]
```
