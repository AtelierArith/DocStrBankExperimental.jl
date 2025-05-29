```
use_system_binary(;
    library_names = ["libmpi", "libmpi_ibm", "msmpi", "libmpich", "libmpi_cray", "libmpitrampoline"],
    extra_paths = String[],
    mpiexec = "mpiexec",
    abi = nothing,
    vendor = nothing,
    export_prefs = false,
    force = true)
```

Switches the underlying MPI implementation to a system provided one. A restart of Julia is required for the changes to take effect.

Options:

  * `library_names`: a name or collection of names of the MPI library, passed to [`Libdl.find_library`](https://docs.julialang.org/en/v1/stdlib/Libdl/#Base.Libc.Libdl.find_library). If the library isn't in the library search path, you can specify the full path to the library.
  * `extra_paths`: indicate extra directories where to search for the MPI library, besides the default ones of the dynamic linker.
  * `mpiexec`: the MPI launcher executable. The default is `mpiexec`, but some clusters require using the scheduler launcher interface (e.g. `srun` on Slurm, `aprun` on PBS). It is also possible to pass a [`Cmd` object](https://docs.julialang.org/en/v1/manual/running-external-programs/#Cmd-Objects) to include specific command line options.
  * `abi`: the ABI of the MPI library. By default this is determined automatically using [`identify_abi`](@ref). See [`abi`](@ref) for currently supported values.
  * `vendor`: can be either `nothing` or a vendor name (such a `"cray"`). If `vendor` has the value "cray", then the output from `cc --cray-print-opts=all` is parsed for which libraries are linked by the Cray Compiler Wrappers. Note that if `mpi_gtl_*` is present, then this .so will be added to the preloads. Also note that the inputs to `library_names` will be overwritten by the library name used by the compiler wrapper.
  * `export_prefs`: if `true`, the preferences into the `Project.toml` instead of `LocalPreferences.toml`.
  * `force`: if `true`, the preferences are set even if they are already set.
