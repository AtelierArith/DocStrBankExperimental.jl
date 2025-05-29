```
@sleefmath expr
```

Execute a transformed version of the expression, which calls functions that may violate strict IEEE semantics and use the [SLEEFPirates](https://github.com/JuliaSIMD/SLEEFPirates.jl) package. This allows the compiler to use SIMD instructions and other optimizations that would not be possible with strict IEEE semantics.

This macro is effective only within loops or broadcasted expressions. If used in for loops, it often requires the use of `@simd ivdep for` loops and `@inbounds` to be effective. For broadcasted expressions, it is often convenient to use `@..` from the [FastBroadcast](https://github.com/YingboMa/FastBroadcast.jl) package.

# Examples

```julia-repl
julia> @sleefmath exp(sin(3.0))
1.151562836514535

julia> xs = rand(10^6); ys = similar(xs);

julia> using BenchmarkTools, FastBroadcast

julia> @btime @.. $ys = @sleefmath exp(sin($xs));
  3.708 ms (0 allocations: 0 bytes)

julia> @btime @.. $ys = exp(sin($xs));
  10.265 ms (0 allocations: 0 bytes)

julia> @btime (@simd ivdep for n ∈ eachindex($xs); @inbounds $ys[n] = @sleefmath exp(sin($xs[n])); end);
  3.719 ms (0 allocations: 0 bytes)
```
