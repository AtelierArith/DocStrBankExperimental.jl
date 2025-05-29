A helper function converting the gate indices from [`graphstate`](@ref) into a Clifford operator.

```jldoctest
julia> s = S" XXX
              YZ_
             -_ZZ";


julia> graph, h_idx, ip_idx, z_idx = graphstate(s);


julia> gate = graph_gate(h_idx, ip_idx, z_idx, nqubits(s));


julia> apply!(s, gate) # This is now a graph state (notice you need to multiply row 1 by row 2)
+ YYZ
+ XZ_
+ _ZX

julia> canonicalize!(s) == canonicalize!(Stabilizer(graph))
true
```

See also: [`graph_gatesequence`](@ref)
