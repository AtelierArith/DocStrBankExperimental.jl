```
build_app_bundle(juliaprog_main;
    appname, builddir, binary_name, resources, libraries, verbose, bundle_identifier,
    app_version, icns_file, certificate, entitlements_file, snoopfile, autosnoop,
    commandline_app, cpu_target)
```

Compile `juliaprog_main` into an executable, and bundle it together with all its `resources` and `libraries` into an App called `appname`.

juliaprog*main: Path to a ".jl" file that defines the function `julia*main()`

# Examples

```julia-repl
julia> build_app_bundle("main.jl", appname="MyApp", resources=["img.jpg"],
           libraries=[MyPackage._libp])
```
