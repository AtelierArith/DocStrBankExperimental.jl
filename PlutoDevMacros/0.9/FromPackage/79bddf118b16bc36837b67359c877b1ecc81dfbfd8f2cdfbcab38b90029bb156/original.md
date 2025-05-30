```
@frompackage target import_block
```

This macro takes a local Package (derived from the `target` path, which can be an `AbstractString` or a `@raw_str`), loads it as a submodule of the current Pluto workspace and then process the various import/using statements inside `import_block` to extract varables/functions from the local Package into the notebook workspace.

Its main use is allowing to load a local package under development within a running Pluto notebook in order to facilitate prototyping and testing.

The following julia code inside a Pluto notebook cell:

```julia
@frompackage local_package_path begin
	import ^: *
	using >.LocalDependency
end
```

takes the main module definition code for the package located at `local_package_path`, creates the corresponding module in the notebook workspace and imports all of the names defined within (That is what the `import ^:*` statement does).

Additionally, it loads the package called `LocalDependency` (must be a dependency of the local package) as if the `using LocalDependency` code was used within the notebook, but without adding `LocalDependency` to the notebook environment.

See the package [documentation](https://disberd.github.io/PlutoDevMacros.jl/dev/frompackage/introduction/#Introduction) for more details.

See also: [`@fromparent`](@ref)
