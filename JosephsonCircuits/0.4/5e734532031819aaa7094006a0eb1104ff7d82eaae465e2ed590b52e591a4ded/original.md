```
parsecircuit(circuit)
```

Parse `circuit` which is a vector where each element contains a tuple with the component name, the first node, the second node, and the component value. Component values can be numbers, symbols, or symbolic variables (including symbolic functions).

The nodes can be arbitrary strings for SPICE compatibility. Integers are also supported but are converted internally to strings. The ground node is "0" and is required. Specifying the type of the vector `circuit` is optional; although, typically a vector with a type union is preferable to an array of type Any.

# Arguments

  * `circuit`: vector of tuples each of which contain the component name, the   first node, the second node, and the component value.

# Examples

```jldoctest
@variables Ipump Rleft L1 K1 L2 C2
circuit = Vector{Tuple{String,String,String,Num}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("L1","1","0",L1))
push!(circuit,("K1","L1","L2",K1))
push!(circuit,("L2","2","0",L2))
push!(circuit,("C2","2","0",C2))
parsecircuit(circuit)

# output
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 2, 0, 0, 3, 2, 3, 2], ["1", "0", "2"], ["L1", "L2"], ["P1", "I1", "R1", "L1", "K1", "L2", "C2"], [:P, :I, :R, :L, :K, :L, :C], Num[1, Ipump, Rleft, L1, K1, L2, C2], Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5), 3)
```

```jldoctest
@variables Ipump Rleft L1 L2 C2
Kfun(L) = sin(L);@register_symbolic Kfun(L1)
circuit = Vector{Tuple{String,String,String,Num}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("L1","1","0",L1))
push!(circuit,("K1","L1","L2",Kfun(L1)))
push!(circuit,("L2","2","0",L2))
push!(circuit,("C2","2","0",C2))
parsecircuit(circuit)

# output
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 2, 0, 0, 3, 2, 3, 2], ["1", "0", "2"], ["L1", "L2"], ["P1", "I1", "R1", "L1", "K1", "L2", "C2"], [:P, :I, :R, :L, :K, :L, :C], Num[1, Ipump, Rleft, L1, Kfun(L1), L2, C2], Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5), 3)
```

```jldoctest
circuit = Vector{Tuple{String,String,String,Union{Complex{Float64}, Symbol,Int}}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",:Ipump))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("C1","1","2",:Cc))
push!(circuit,("Lj1","2","0",:Lj))
push!(circuit,("C2","2","0",:Cj))
parsecircuit(circuit)

# output
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 3, 3, 2, 3, 2], ["1", "0", "2"], String[], ["P1", "I1", "R1", "C1", "Lj1", "C2"], [:P, :I, :R, :C, :Lj, :C], Union{Int64, Symbol, ComplexF64}[1, :Ipump, :Rleft, :Cc, :Lj, :Cj], Dict("I1" => 2, "C1" => 4, "C2" => 6, "R1" => 3, "P1" => 1, "Lj1" => 5), 3)
```

```jldoctest
circuit = Vector{Tuple{String,String,String,Union{Complex{Float64}, Symbol,Int}}}(undef,0)
push!(circuit,("P1","One","0",1))
push!(circuit,("I1","One","0",:Ipump))
push!(circuit,("R1","One","0",:Rleft))
push!(circuit,("C1","One","Two",:Cc))
push!(circuit,("Lj1","Two","0",:Lj))
push!(circuit,("C2","Two","0",:Cj))
parsecircuit(circuit)

# output
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 3, 3, 2, 3, 2], ["One", "0", "Two"], String[], ["P1", "I1", "R1", "C1", "Lj1", "C2"], [:P, :I, :R, :C, :Lj, :C], Union{Int64, Symbol, ComplexF64}[1, :Ipump, :Rleft, :Cc, :Lj, :Cj], Dict("I1" => 2, "C1" => 4, "C2" => 6, "R1" => 3, "P1" => 1, "Lj1" => 5), 3)
```

```jldoctest
circuit = []
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",:Ipump))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("C1","1","2",:Cc))
push!(circuit,("Lj1","2","0",:Lj))
push!(circuit,("C2","2","0",:Cj))
parsecircuit(circuit)

# output
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 3, 3, 2, 3, 2], ["1", "0", "2"], String[], ["P1", "I1", "R1", "C1", "Lj1", "C2"], [:P, :I, :R, :C, :Lj, :C], Any[1, :Ipump, :Rleft, :Cc, :Lj, :Cj], Dict("I1" => 2, "C1" => 4, "C2" => 6, "R1" => 3, "P1" => 1, "Lj1" => 5), 3)
```

```jldoctest
circuit = Vector{Tuple{String,String,String,Union{Complex{Float64}, Symbol,Int}}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",:Ipump))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("L1","1","0",:L1))
push!(circuit,("K1","L1","L2",:K1))
push!(circuit,("L2","2","0",:L2))
push!(circuit,("C2","2","0",:C2))
parsecircuit(circuit)

# output
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 2, 0, 0, 3, 2, 3, 2], ["1", "0", "2"], ["L1", "L2"], ["P1", "I1", "R1", "L1", "K1", "L2", "C2"], [:P, :I, :R, :L, :K, :L, :C], Union{Int64, Symbol, ComplexF64}[1, :Ipump, :Rleft, :L1, :K1, :L2, :C2], Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5), 3)
```
