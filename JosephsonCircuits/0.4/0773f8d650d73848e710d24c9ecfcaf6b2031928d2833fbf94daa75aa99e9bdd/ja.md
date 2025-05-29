```
numericmatrices(circuit, circuitdefs; Nmodes = 1, sorting = :number)
```

回路特性を説明する数値行列を返します。

関連情報としては、[`CircuitMatrices`](@ref)、[`numericmatrices`](@ref)、[`calcCn`](@ref)、[`calcGn`](@ref)、[`calcLb`](@ref)、[`calcLjb`](@ref)、[`calcMb`](@ref)、[`calcinvLn`](@ref)、[`calcLmean`](@ref)、[`calcportindicesnumbers`](@ref)、[`calcportimpedanceindices`](@ref)、および[`calcnoiseportimpedanceindices`](@ref)があります。

# 例

```jldoctest
@variables Ipump Rleft Cc Lj Cj
circuit = Vector{Tuple{String,String,String,Num}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("C1","1","2",Cc)) 
push!(circuit,("Lj1","2","0",Lj)) 
push!(circuit,("C2","2","0",Cj))
circuitdefs = Dict(Lj =>1000.0e-12,Cc => 100.0e-15,Cj => 1000.0e-15,Rleft => 50.0,Ipump => 1.0e-8)
JosephsonCircuits.testshow(stdout,numericmatrices(circuit,circuitdefs))

# 出力
JosephsonCircuits.CircuitMatrices(sparse([1, 2, 1, 2], [1, 1, 2, 2], [1.0e-13, -1.0e-13, -1.0e-13, 1.1e-12], 2, 2), sparse([1], [1], [0.02], 2, 2), sparsevec(Int64[], Nothing[], 2), sparsevec(Int64[], Nothing[], 2), sparsevec([2], [1.0e-9], 2), sparsevec([2], [1.0e-9], 2), sparse(Int64[], Int64[], Nothing[], 2, 2), sparse(Int64[], Int64[], Nothing[], 2, 2), sparse([1, 2], [1, 2], [1, 1], 2, 2), [1], [1], [3], Int64[], 1.0e-9, Real[1, 1.0e-8, 50.0, 1.0e-13, 1.0e-9, 1.0e-12])
```

```jldoctest
@variables Ipump Rleft Cc Lj Cj
circuit = Vector{Tuple{String,String,String,Num}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("C1","1","2",Cc)) 
push!(circuit,("Lj1","2","0",Lj)) 
push!(circuit,("C2","2","0",Cj))
circuitdefs = Dict(Lj =>1000.0e-12,Cc => 100.0e-15,Cj => 1000.0e-15,Rleft => 50.0,Ipump => 1.0e-8)
psc = JosephsonCircuits.parsesortcircuit(circuit)
cg = JosephsonCircuits.calccircuitgraph(psc)
JosephsonCircuits.testshow(stdout,numericmatrices(psc, cg, circuitdefs))

# 出力
JosephsonCircuits.CircuitMatrices(sparse([1, 2, 1, 2], [1, 1, 2, 2], [1.0e-13, -1.0e-13, -1.0e-13, 1.1e-12], 2, 2), sparse([1], [1], [0.02], 2, 2), sparsevec(Int64[], Nothing[], 2), sparsevec(Int64[], Nothing[], 2), sparsevec([2], [1.0e-9], 2), sparsevec([2], [1.0e-9], 2), sparse(Int64[], Int64[], Nothing[], 2, 2), sparse(Int64[], Int64[], Nothing[], 2, 2), sparse([1, 2], [1, 2], [1, 1], 2, 2), [1], [1], [3], Int64[], 1.0e-9, Real[1, 1.0e-8, 50.0, 1.0e-13, 1.0e-9, 1.0e-12])
```
