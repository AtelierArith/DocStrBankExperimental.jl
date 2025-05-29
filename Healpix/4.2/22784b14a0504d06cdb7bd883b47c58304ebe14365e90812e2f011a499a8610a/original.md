```
interpolate(m::HealpixMap{T, RingOrder, AA}, θ, ϕ) -> Value
interpolate(m::HealpixMap{T, RingOrder, AA}, θ, ϕ, pixbuf, weightbuf) -> Value
```

Return an interpolated value of the map along the specified direction.

When provided, the parameters `pixbuf` and `weightbuf` must be 4-element arrays of integer and floating-point values, respectively. They can be reused across multiple calls of `interpolate`, to save heap allocations, and they do not need to be initialized, as they are used internally:

```
pixbuf = Array{Int}(undef, 4)
weightbuf = Array{Float64}(undef, 4)

m = HealpixMap{Float64, RingOrder}(1)
for (θ, ϕ) in [(0., 0.), (π/2, π/2)]
    println(interpolate(m, θ, ϕ, pixbuf, weightbuf))
end
```

Passing `pixbuf` and `weightbuf` saves some time, as this simple benchmark shows:

```
julia> @benchmark interpolate(m, rand(), rand(), pixbuf, weightbuf)
BenchmarkTools.Trial:
  memory estimate:  618 bytes
  allocs estimate:  9
  --------------
  minimum time:     283.184 ns (0.00% GC)
  median time:      296.140 ns (0.00% GC)
  mean time:        348.132 ns (9.55% GC)
  maximum time:     10.627 μs (95.88% GC)
  --------------
  samples:          10000
  evals/sample:     282

julia> @benchmark interpolate(m, rand(), rand())
BenchmarkTools.Trial:
  memory estimate:  837 bytes
  allocs estimate:  11
  --------------
  minimum time:     329.825 ns (0.00% GC)
  median time:      345.504 ns (0.00% GC)
  mean time:        417.004 ns (11.04% GC)
  maximum time:     13.733 μs (96.21% GC)
  --------------
  samples:          10000
  evals/sample:     223
```
