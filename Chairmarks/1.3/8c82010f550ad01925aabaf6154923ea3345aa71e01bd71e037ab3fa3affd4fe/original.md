```
@b [[init] setup] f [teardown] keywords...
```

Benchmark `f` and return the fastest [`Sample`](@ref).

Use [`@be`](@ref) for full results.

`@b args...` is equivalent to `Chairmarks.summarize(@be args...)`. See the docstring of [`@be`](@ref) for more information.

# Examples

```jldoctest; filter = [r"\d\d?\d?\.\d{3} [μmn]?s( \(.*\))?"=>s"RES"], setup=(using Random)
julia> @b rand(10000) # Benchmark a function
5.833 μs (2 allocs: 78.172 KiB)

julia> @b rand hash # How long does it take to hash a random Float64?
1.757 ns

julia> @b rand(1000) sort issorted(_) || error() # Simultaneously benchmark and test
11.291 μs (3 allocs: 18.062 KiB)

julia> @b rand(1000) sort! issorted(_) || error() # BAD! This repeatedly resorts the same array!
1.309 μs (0.08 allocs: 398.769 bytes)

julia> @b rand(1000) sort! issorted(_) || error() evals=1 # Specify evals=1 to ensure the function is only run once between setup and teardown
10.041 μs (2 allocs: 10.125 KiB)

julia> @b rand(10) _ sort!∘rand! issorted(_) || error() # Or, include randomization in the benchmarked function and only allocate once
120.536 ns

julia> @b (x = 0; for _ in 1:50; x = hash(x); end; x) # We can use arbitrary expressions in any position in the pipeline, not just simple functions.
183.871 ns

julia> @b (x = 0; for _ in 1:5e8; x = hash(x); end; x) # This runs for a long time, so it is only run once (with no warmup)
2.447 s (without a warmup)

julia> @b rand(10) hash,objectid # Which hash algorithm is faster? [THIS USAGE IS EXPERIMENTAL]
(17.256 ns, 4.246 ns)
```
