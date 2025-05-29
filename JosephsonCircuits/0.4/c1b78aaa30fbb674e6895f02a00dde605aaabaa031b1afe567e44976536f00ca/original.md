```
calccircuitgraph(parsedsortedcircuit::ParsedSortedCircuit)
```

Calculate the superconducting spanning tree, incidence matrix, closure branches, and loops from the parsed and sorted circuit.

See also [`CircuitGraph`](@ref), [`calcgraphs`](@ref), and [`extractbranches`](@ref)  for more explanation.

# Examples

```jldoctest
@variables Ipump Rleft L1 K1 L2 C2
psc = JosephsonCircuits.ParsedSortedCircuit(
    [2 2 2 2 0 3 3; 1 1 1 1 0 1 1],
    ["0", "1", "2"],
    ["L1", "L2"],
    ["P1", "I1", "R1", "L1", "K1", "L2", "C2"],
    [:P, :I, :R, :L, :K, :L, :C],
    Num[1, Ipump, Rleft, L1, K1, L2, C2],
    Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5),
    3)
cg = JosephsonCircuits.calccircuitgraph(psc)
# output
JosephsonCircuits.CircuitGraph(Dict((1, 2) => 1, (3, 1) => 2, (1, 3) => 2, (2, 1) => 1), sparse([1, 2], [1, 2], [1, 1], 2, 2), [(1, 2), (1, 3)], Tuple{Int64, Int64}[], [(1, 2), (1, 3)], Vector{Int64}[], Int64[], Graphs.SimpleGraphs.SimpleGraph{Int64}(2, [[2, 3], [1], [1]]), 2)
```

```jldoctest
@variables Ipump Rleft L Lj Cj
circuit = Tuple{String,String,String,Num}[]
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("L1","1","2",L))
push!(circuit,("Lj1","2","0",Lj))
push!(circuit,("C2","2","0",Cj))
psc = JosephsonCircuits.parsesortcircuit(circuit)
cg = JosephsonCircuits.calccircuitgraph(psc)
# output
JosephsonCircuits.CircuitGraph(Dict((3, 2) => 3, (1, 2) => 1, (3, 1) => 2, (1, 3) => 2, (2, 1) => 1, (2, 3) => 3), sparse([1, 3, 2, 3], [1, 1, 2, 2], [1, -1, 1, 1], 3, 2), [(1, 2), (1, 3)], [(3, 2)], [(1, 2), (1, 3), (2, 3)], [[1, 2, 3]], Int64[], Graphs.SimpleGraphs.SimpleGraph{Int64}(3, [[2, 3], [1, 3], [1, 2]]), 3)
```
