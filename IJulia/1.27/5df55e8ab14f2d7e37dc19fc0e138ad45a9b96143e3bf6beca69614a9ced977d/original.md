```
installkernel(name::AbstractString, options::AbstractString...;
              julia::Cmd,
              specname::AbstractString,
              displayname::AbstractString,
              env=Dict())
```

Install a new Julia kernel, where the given `options` are passed to the `julia` executable, the user-visible kernel name is given by `name` followed by the Julia version, and the `env` dictionary is added to the environment.

The new kernel name is returned by `installkernel`.  For example:

```julia
kernelpath = installkernel("Julia O3", "-O3", env=Dict("FOO"=>"yes"))
```

creates a new Julia kernel in which `julia` is launched with the `-O3` optimization flag and `FOO=yes` is included in the environment variables.

The `displayname` argument can be used to customize the name displayed in the Jupyter kernel list.

The returned `kernelpath` is the path of the installed kernel directory, something like `/...somepath.../kernels/julia-o3-1.6` (in Julia 1.6).  The `specname` argument can be passed to alter the name of this directory (which defaults to `name` with spaces replaced by hyphens, and special characters other than `-` hyphen, `.` period and `_` underscore replaced by `_` underscores).

You can uninstall the kernel by calling `rm(kernelpath, recursive=true)`.

You can specify a custom command to execute Julia via keyword argument `julia`. For example, you may want specify that the Julia kernel is running in a Docker container (but Jupyter will run outside of it), by calling `installkernel` from within such a container instance like this (or similar):

```julia
installkernel(
    "Julia via Docker",
    julia = `docker run --rm --net=host
        --volume=/home/USERNAME/.local/share/jupyter:/home/USERNAME/.local/share/jupyter
        some-container /opt/julia-1.x/bin/julia`
)
```
