```
faulhaber(m, ::Val{p})
```

Compute the summation `sum(i->i^p, 1:m)` in $O(p)$ time. When `m` is an integer, the function returns an exact integer solution assuming integer overflows don't occur. When `m` is a floating-point number, then it returns a less accurate float solution.

Examples:

```julia
julia> using BenchmarkTools, Faulhaber

julia> @btime faulhaber(Ref(Int128(2000))[], Val(7))
  1.143 ns (0 allocations: 0 bytes)
32064037333328666667000000

julia> @btime sum(i->i^7, 1:Int128(2000))
  12.282 μs (0 allocations: 0 bytes)
32064037333328666667000000

julia> @btime faulhaber(Ref(2000.0)[], Val(7))
  1.134 ns (0 allocations: 0 bytes)
3.2064037333328662e25
```
