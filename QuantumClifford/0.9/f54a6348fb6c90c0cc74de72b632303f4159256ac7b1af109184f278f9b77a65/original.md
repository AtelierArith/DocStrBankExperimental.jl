A helper function converting the gate indices from [`graphstate`](@ref) into a sequence of gates.

```jldoctest
julia> s = S" XXX
              YZ_
             -_ZZ";


julia> graph, h_idx, ip_idx, z_idx = graphstate(s);


julia> gates = graph_gatesequence(h_idx, ip_idx, z_idx);


julia> for gate in vcat(gates...) apply!(s, gate) end


julia> s # This is now a graph state (notice you need to multiply row 1 by row 2)
+ YYZ
+ XZ_
+ _ZX

julia> canonicalize!(s) == canonicalize!(Stabilizer(graph))
true
```

See also: [`graph_gatesequence`](@ref)
