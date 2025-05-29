```
struct Benchmark
    samples::Vector{Sample}
    ...more fields may be added...
end
```

A struct representing a complete benchmark result. Returned by [`@be`](@ref).

More fields may be added in the future to represent non sample specific information.

The functions `minimum` and `maximum` are defined field wise on `Benchmark` objects and return [`Sample`](@ref)s. On Julia 1.9 and above, the functions `Statistics.median`, `Statistics.mean`, and `Statistics.quantile` are also defined field wise on `Benchmark` objects and return `Sample`s.

```jldoctest; filter = [r"\d\d?\d?\.\d{3} [μmn]?s( \(.*\))?"=>s"RES", r"\d+ (sample|evaluation)s?"=>s"### \1"]
julia> @be eval(:(for _ in 1:10; sqrt(rand()); end))
Benchmark: 15 samples with 1 evaluation
 min    4.307 ms (3608 allocs: 173.453 KiB, 92.21% compile time)
 median 4.778 ms (3608 allocs: 173.453 KiB, 94.65% compile time)
 mean   6.494 ms (3608 allocs: 173.453 KiB, 94.15% compile time)
 max    12.021 ms (3608 allocs: 173.453 KiB, 95.03% compile time)

julia> minimum(ans)
4.307 ms (3608 allocs: 173.453 KiB, 92.21% compile time)
```
