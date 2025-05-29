Run a package test-suite in a subprocess.

```julia
test(
    file="test/runtests.jl";
    root=pwd(),
    project="test",
    code_coverage=".coverage/tracefile-%p.info",
    show_coverage=(code_coverage != "none"),
    color=<inherit>,
    compiled_modules=<inherit>,
    startup_file=<inherit>,
    depwarn=<inherit>,
    inline=<inherit>,
    check_bounds="yes",
    track_allocation=<inherit>,
    threads=<inherit>,
    genhtml=false,
    covdir="coverage"
)
```

runs the test suite of the package located at `root` by running `include(file)` inside a new julia process.

This is similar to what `Pkg.test()` does, but differs in the "sandboxing" approach. While `Pkg.test()` creates a new temporary sandboxed environment, `test()` uses an existing environment in `project` (the `test` subfolder by default). This allows testing against the dev-versions of other packages. It requires that the `test` folder contains both a `Project.toml` and a `Manifest.toml` file.

The `test()` function also differs from directly including `test/runtests.jl` in the REPL in that it can generate coverage data and reports (this is only possible when running tests in a subprocess).

If `show_coverage` is passed as `true` (default), a coverage summary is shown. Further, if `genhtml` is `true`, a full HTML coverage report will be generated in `covdir` (relative to `root`). This requires the `genhtml` executable (part of the [lcov](http://ltp.sourceforge.net/coverage/lcov.php) package). Instead of `true`, it is also possible to pass the path to the `genhtml` executable.

All other keyword arguments correspond to the respective command line flag for the `julia` executable that is run as the subprocess.

This function is intended to be exposed in a project's development-REPL.
