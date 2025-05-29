Convert any stabilizer state to a graph state

[Graph states](https://en.wikipedia.org/wiki/Graph_state) are a special type of entangled stabilizer states that can be represented by a graph. For a graph $G=(V,E)$ the corresponding stabilizers are $S_v = X_v \prod_{u ∈ N(v)} Z_u$. Notice that such tableau rows contain only a single X operator. There is a set of single qubit gates that converts any stabilizer state to a graph state.

This function returns the graph state corresponding to a stabilizer and the gates that might be necessary to convert the stabilizer into a state representable as a graph.

For a tableau `stab` you can convert it with:

```julia
graph, hadamard_idx, iphase_idx, flips_idx = graphstate()
```

where `graph` is the graph representation of `stab`, and the rest specifies the single-qubit gates converting `stab` to `graph`: `hadamard_idx` are the qubits that require a Hadamard gate (mapping X ↔ Z), `iphase_idx` are (different) qubits that require an inverse Phase gate (Y → X), and `flips_idx` are the qubits that require a phase flip (Pauli Z gate), after the previous two sets of gates.

```jldoctest graph
julia> using Graphs

julia> s = S" XXX
              ZZ_
             -_ZZ";


julia> g, h_idx, ip_idx, z_idx = graphstate(s);


julia> collect(edges(g))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3

julia> h_idx
2-element Vector{Int64}:
 2
 3

julia> ip_idx
Int64[]

julia> z_idx
1-element Vector{Int64}:
 3
```

The `Graphs.jl` library provides many graph-theory tools and the `MakieGraphs.jl` library provides plotting utilities for graphs.

You can directly call the graph constructor on a stabilizer, if you just want the graph and do not care about the Clifford operation necessary to convert an arbitrary state to a state representable as a graph:

```jldoctest graph
julia> collect(edges( Graph(bell()) ))
1-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
```

For a version that does not copy the stabilizer, but rather performs transformations in-place, use `graphstate!`. It would perform `canonicalize_gott!` on its argument as it finds a way to convert it to a graph state.
