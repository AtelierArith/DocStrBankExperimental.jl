```
signal(spin)
signal(M)
```

Return the signal detected from the given spin or magnetization vector.

# Examples

```jldoctest
julia> signal(Spin(Magnetization(1, 2, 3), 1, 1000, 100, 0))
1.0 + 2.0im

julia> signal(MagnetizationMC((1, 2, 3), (1, 1, 1)))
2 + 3im
```
