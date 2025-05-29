```julia
struct OutputConfig
```

struct containing information about what to output.

There are two possible output formats:

  * .npy files that use numpy's format. They can be read with [`NPZ`](https://github.com/fhs/NPZ.jl).
  * HDF5 files that can be read with [`HDF5`](https://github.com/JuliaIO/HDF5.jl).

Each member of `summary_statistics` should be another struct whose constructor generates summary statistics from `t`, `a`, `Δt` and a `grids` object. If it is to be used with a [`PencilGrids`](@ref) object, each field must be concrete and have a binary representation that MPI can handle.

By default, `summary_statistics` will write only the wall time and simulation time.

# Fields

  * `directory::String`: where to write output
  * `output_times::Array{Float64}`: times at which to output
  * `box::Bool`: whether to output boxes
  * `slice::Bool`: whether to output slices
  * `psi::Bool`: whether to output ψ
  * `rho::Bool`: whether to output ρ
  * `npy::Bool`: write .npy files
  * `h5::Bool`: write HDF5 files
  * `summary_statistics::Tuple`: Type of summary statistics to collect
