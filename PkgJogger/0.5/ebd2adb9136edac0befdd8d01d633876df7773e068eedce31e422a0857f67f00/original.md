```
@jog PkgName
```

Creates a module named `JogPkgName` for running benchmarks for `PkgName`.

Most edits to benchmark files are correctly tracked by Revise.jl. If they are not, re-run `@jog PkgName` to fully reload `JogPkgName`.

> Revise must be loaded before calling `@jog PkgName` in order for edits to be automatically tracked.


## Methods

  * `suite`       Return a `BenchmarkGroup` of the benchmarks for `PkgName`
  * `benchmark`   Warmup, tune and run the suite
  * `run`         Dispatch to `BenchmarkTools.run(suite(), args...; kwargs...)`
  * `save_benchmarks`     Save benchmarks for `PkgName` using an unique filename

## Isolated Benchmarks

Each benchmark file, is wrapped in it's own module preventing code loaded in one file from being visible in another (unless explicitly included).

## Example

```julia
using AwesomePkg, PkgJogger
@jog AwesomePkg
results = JogAwesomePkg.benchmark()
file = JogAwesomePkg.save_benchmarks(results)
```
