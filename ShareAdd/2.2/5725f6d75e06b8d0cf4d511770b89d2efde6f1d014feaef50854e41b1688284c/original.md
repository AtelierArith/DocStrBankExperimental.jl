```
Package ShareAdd v2.2.0
```

This Julia package exports macro `@usingany`. This macro makes package(s) available, if they are not already, and loads  them with `using` keyword. 

  * If a package is available in an environment in `LOAD_PATH`, that's OK.
  * If a package is available in a shared environment, this environment will be pushed into `LOAD_PATH`.
  * Otherwise if package(s) can be installed, you will be prompted to select an environment to install each package.
  * If the package is not listed in any registry, an error will be thrown.

There are also utility functions in ShareAdd that may help you manage shared environments, i.a.:

  * [`ShareAdd.info`](@ref): lists information about shared envs and/or packages.
  * [`ShareAdd.update`](@ref): updates packages or environments
  * [`ShareAdd.delete`](@ref): deletes packages or environments
  * [`@showenv`](@ref): opens environment folders in your desktop GUI.

The functions are public, but not exported to avoid possible name conflicts. The `@showenv` macro is exported.

# Examples

```julia-repl
julia> ShareAdd.update("Plots")
  Activating project at `~/.julia/environments/Plotting`
# ... a screenful of update information
julia> @usingany Plots
julia> plot(xs, ys)
```

Reference: see docstrings.

Documentation: https://eben60.github.io/ShareAdd.jl/

Package local path: /home/terasaki/.julia/packages/ShareAdd/UJfFT/src/ShareAdd.jl
