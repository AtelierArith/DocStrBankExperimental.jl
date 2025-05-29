```
num_occupied_modes(::SingleComponentFockAddress)
```

Get the number of occupied modes in address. Equivalent to `length(`[`occupied_modes`](@ref)`(address))`, or the number of non-zeros in its ONR representation.

# Example

```jldoctest
julia> num_occupied_modes(BoseFS((1, 0, 2)))
2
julia> num_occupied_modes(FermiFS((1, 1, 1, 0)))
3
```

See [`SingleComponentFockAddress`](@ref).
