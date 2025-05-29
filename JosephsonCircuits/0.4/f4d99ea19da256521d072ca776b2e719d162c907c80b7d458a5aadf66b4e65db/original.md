```
parsesortcircuit(circuit; sorting = :name)
```

Parse and sort the circuit. See [`parsecircuit`](@ref), [`sortnodes`](@ref) for more explanation.

# Arguments

  * `circuit`: vector of tuples each of which contain the component name, the   first node, the second node, and the component value. The first three must   be strings.

# Keywords

  * `sorting = :name`: Sort the vector of strings. This always works but leads   to results like "101" comes before "11".
  * `sorting = :number`: Convert the node strings to integer and sort by these   (this errors if the nodes names cannot be converted to integers).
  * `sorting = :none`: Don't perform any sorting except to place the ground node   first. In other words, order the nodes in the order they are found in   `circuit`.

# Examples

```jldoctest
@variables Ipump Rleft Cc Lj Cj
circuit = Tuple{String,String,String,Num}[]
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("C1","1","2",Cc))
push!(circuit,("Lj1","2","0",Lj))
push!(circuit,("C2","2","0",Cj))
println(parsesortcircuit(circuit))

# output
JosephsonCircuits.ParsedSortedCircuit([2 2 2 2 3 3; 1 1 1 3 1 1], ["0", "1", "2"], String[], ["P1", "I1", "R1", "C1", "Lj1", "C2"], [:P, :I, :R, :C, :Lj, :C], Num[1, Ipump, Rleft, Cc, Lj, Cj], Dict("I1" => 2, "C1" => 4, "C2" => 6, "R1" => 3, "P1" => 1, "Lj1" => 5), 3)
```

```jldoctest
@variables Ipump Rleft L1 L2 C2
Kfun(L) = sin(L);@register_symbolic Kfun(L1)
circuit = Tuple{String,String,String,Num}[]
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("L1","1","0",L1)) 
push!(circuit,("K1","L1","L2",Kfun(L1)))
push!(circuit,("L2","2","0",L2)) 
push!(circuit,("C2","2","0",C2))
println(parsesortcircuit(circuit))

# output
JosephsonCircuits.ParsedSortedCircuit([2 2 2 2 0 3 3; 1 1 1 1 0 1 1], ["0", "1", "2"], ["L1", "L2"], ["P1", "I1", "R1", "L1", "K1", "L2", "C2"], [:P, :I, :R, :L, :K, :L, :C], Num[1, Ipump, Rleft, L1, Kfun(L1), L2, C2], Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5), 3)
```
