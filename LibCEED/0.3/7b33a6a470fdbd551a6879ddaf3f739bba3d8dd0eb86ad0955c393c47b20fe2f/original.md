```
set_libceed_path!(path::AbstractString)
set_libceed_path!(:prebuilt)
set_libceed_path!(:default)
```

Sets the path of the libCEED dynamic library. `path` should be the absolute path to the library file.

`set_libceed_path!(:prebuilt)` indicates to LibCEED.jl to use the prebuilt version of the libCEED library (bundled with libCEED_jll).

`set_libceed_path!(:default)` indicates to LibCEED.jl to use the default library. This usually has the same effect as `set_libceed_path!(:prebuilt)`, unless a different path has been specified in the depot-wide preferences or using [Overrides.toml](https://pkgdocs.julialang.org/dev/artifacts/#Overriding-artifact-locations).

This function sets the library path as a *preference* associated with the currently active environment. Changes will take effect after restarting the Julia session. See the [Preferences.jl documentation](https://github.com/JuliaPackaging/Preferences.jl) for more information.
