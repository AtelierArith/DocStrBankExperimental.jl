```
LatticeRule32(file, s, n)
LatticeRule32(file, s)
LatticeRule32(file)
```

Returns a rank-1 lattice rule in `s` dimensions with generating vector `z` read from the file `file` and with at most `n` points.

# Examples

```jldoctest; setup = :(using LatticeRules)
julia> z_file = K_3600_32_file;

julia> lattice_rule = LatticeRule32(z_file, 16)
LatticeRule32{16}

julia> getpoint(lattice_rule, 123)
16-element Array{Float64,1}:
 0.8671875
 0.9609375
 0.6015625
 0.8984375
 0.6484375
 0.6328125
 0.3203125
 0.2890625
 0.0234375
 0.1015625
 0.7890625
 0.0703125
 0.6953125
 0.0234375
 0.1171875
 0.0859375

```

See also: [`getpoint`](@ref), [`ShiftedLatticeRule32`](@ref)
