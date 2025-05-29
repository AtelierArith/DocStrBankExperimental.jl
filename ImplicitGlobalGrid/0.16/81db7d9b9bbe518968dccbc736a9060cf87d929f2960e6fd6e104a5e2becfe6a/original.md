```
init_global_grid(nx, ny, nz)
me, dims, nprocs, coords, comm_cart = init_global_grid(nx, ny, nz; <keyword arguments>)
```

Initialize a Cartesian grid of MPI processes (and also MPI itself by default) defining implicitely a global grid.

# Arguments

  * {`nx`|`ny`|`nz`}`::Integer`: the number of elements of the local grid in dimension {x|y|z}.
  * {`dimx`|`dimy`|`dimz`}`::Integer=0`: the desired number of processes in dimension {x|y|z}. By default, (value `0`) the process topology is created as compact as possible with the given constraints. This is handled by the MPI implementation which is installed on your system. For more information, refer to the specifications of `MPI_Dims_create` in the corresponding documentation.
  * {`periodx`|`periody`|`periodz`}`::Integer=0`: whether the grid is periodic (`1`) or not (`0`) in dimension {x|y|z}.
  * `quiet::Bool=false`: whether to suppress printing information like the size of the global grid (`true`) or not (`false`).

!!! note "Advanced keyword arguments"
      * `overlaps::Tuple{Int,Int,Int}=(2,2,2)`: the number of elements adjacent local grids overlap in dimension x, y and z. By default (value `(2,2,2)`), an array `A` of size (`nx`, `ny`, `nz`) on process 1 (`A_1`) overlaps the corresponding array `A` on process 2 (`A_2`) by `2` indices if the two processes are adjacent. E.g., if `overlaps[1]=2` and process 2 is the right neighbor of process 1 in dimension x, then `A_1[end-1:end,:,:]` overlaps `A_2[1:2,:,:]`. That means, after every call `update_halo!(A)`, we have `all(A_1[end-1:end,:,:] .== A_2[1:2,:,:])` (`A_1[end,:,:]` is the halo of process 1 and `A_2[1,:,:]` is the halo of process 2). The analog applies for the dimensions y and z.
      * `halowidths::Tuple{Int,Int,Int}=max.(1,overlaps.÷2)`: the default width of an array's halo in dimension x, y and z (must be greater than 1). The default can be overwritten per array in the function [`update_halo`](@ref).
      * `disp::Integer=1`:  the displacement argument to `MPI.Cart_shift` in order to determine the neighbors.
      * `reorder::Integer=1`: the reorder argument to `MPI.Cart_create` in order to create the Cartesian process topology.
      * `comm::MPI.Comm=MPI.COMM_WORLD`: the input communicator argument to `MPI.Cart_create` in order to create the Cartesian process topology.
      * `init_MPI::Bool=true`: whether to initialize MPI (`true`) or not (`false`).
      * `device_type::String="auto"`: the type of the device to be used if available: `"CUDA"`, `"AMDGPU"`, `"none"` or `"auto"`. Set `device_type="none"` if you want to use only CPUs on a system having also GPUs. If `device_type` is `"auto"` (default), it is automatically determined, depending on which of the modules used for programming the devices (CUDA.jl or AMDGPU.jl) was imported before ImplicitGlobalGrid; if both were imported, an error will be given if `device_type` is set as `"auto"`.
      * `select_device::Bool=true`: whether to automatically select the device (GPU) (`true`) or not (`false`) if CUDA or AMDGPU was imported and `device_type` is not `"none"`. If `true`, it selects the device corresponding to the node-local MPI rank. This method of device selection suits both single and multi-device compute nodes and is recommended in general. It is also the default method of device selection of the *function* [`select_device`](@ref).

    For more information, refer to the documentation of MPI.jl / MPI.


# Return values

  * `me`: the MPI rank of the process.
  * `dims`: the number of processes in each dimension.
  * `nprocs`: the number of processes.
  * `coords`: the Cartesian coordinates of the process.
  * `comm_cart`: the MPI communicator of the created Cartesian process topology.

# Typical use cases

```
init_global_grid(nx, ny, nz)                  # Basic call (no optional in and output arguments).
me, = init_global_grid(nx, ny, nz)            # Capture 'me' (note the ','!).
me, dims = init_global_grid(nx, ny, nz)       # Capture 'me' and 'dims'.
init_global_grid(nx, ny, nz; dimx=2, dimy=2)  # Fix the number of processes in the dimensions x and y of the Cartesian grid of MPI processes to 2 (the number of processes can vary only in the dimension z).
init_global_grid(nx, ny, nz; periodz=1)       # Make the boundaries in dimension z periodic.
```

See also: [`finalize_global_grid`](@ref), [`select_device`](@ref)
