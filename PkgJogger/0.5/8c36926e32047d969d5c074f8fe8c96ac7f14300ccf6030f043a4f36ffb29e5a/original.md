```
@test_benchmarks PkgName
```

Collects all benchmarks for `PkgName`, and test that they don't error when ran once.

## Example

```julia-repl
julia> using PkgJogger, Example

julia> @test_benchmarks Example
│ Test Summary:  | Pass  Total
│ bench_timer.jl |    2      2
[...]
```

## Testing

Each benchmark is wrapped in a `@testset`, run only once, and marked as passing iff no errors are raised. This provides a fast smoke test for a benchmarking suite, and avoids the usual cost of tunning, warming up and collecting samples accrued when actually benchmarking.

## Benchmark Loading

Locating benchmarks for testing is the same as for [`@jog`](@ref) and can be examined using [`PkgJogger.locate_benchmarks`](@ref).
