```
symbolicmatrices(circuit; Nmodes = 1, sorting = :number)
```

回路特性を記述する記号行列を返します。

参照してください [`CircuitMatrices`](@ref), [`numericmatrices`](@ref), [`calcCn`](@ref), [`calcGn`](@ref), [`calcLb`](@ref),[`calcLjb`](@ref), [`calcMb`](@ref), [`calcinvLn`](@ref), [`calcLmean`](@ref), [`calcportindicesnumbers`](@ref), [`calcportimpedanceindices`](@ref), および [`calcnoiseportimpedanceindices`](@ref)。

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
JosephsonCircuits.testshow(stdout,symbolicmatrices(circuit))

# 出力
JosephsonCircuits.CircuitMatrices(sparse([1, 2, 1, 2], [1, 1, 2, 2], SymbolicUtils.BasicSymbolic{Real}[Cc, -Cc, -Cc, Cc + Cj], 2, 2), sparse([1], [1], SymbolicUtils.BasicSymbolic{Real}[1 / Rleft], 2, 2), sparsevec(Int64[], Nothing[], 2), sparsevec(Int64[], Nothing[], 2), sparsevec([2], SymbolicUtils.BasicSymbolic{Real}[Lj], 2), sparsevec([2], SymbolicUtils.BasicSymbolic{Real}[Lj], 2), sparse(Int64[], Int64[], Nothing[], 2, 2), sparse(Int64[], Int64[], Nothing[], 2, 2), sparse([1, 2], [1, 2], [1, 1], 2, 2), [1], [1], [3], Int64[], Lj, Any[1, Ipump, Rleft, Cc, Lj, Cj])
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
psc = JosephsonCircuits.parsesortcircuit(circuit)
cg = JosephsonCircuits.calccircuitgraph(psc)
JosephsonCircuits.testshow(stdout,symbolicmatrices(psc, cg))

# 出力
JosephsonCircuits.CircuitMatrices(sparse([1, 2, 1, 2], [1, 1, 2, 2], SymbolicUtils.BasicSymbolic{Real}[Cc, -Cc, -Cc, Cc + Cj], 2, 2), sparse([1], [1], SymbolicUtils.BasicSymbolic{Real}[1 / Rleft], 2, 2), sparsevec(Int64[], Nothing[], 2), sparsevec(Int64[], Nothing[], 2), sparsevec([2], SymbolicUtils.BasicSymbolic{Real}[Lj], 2), sparsevec([2], SymbolicUtils.BasicSymbolic{Real}[Lj], 2), sparse(Int64[], Int64[], Nothing[], 2, 2), sparse(Int64[], Int64[], Nothing[], 2, 2), sparse([1, 2], [1, 2], [1, 1], 2, 2), [1], [1], [3], Int64[], Lj, Any[1, Ipump, Rleft, Cc, Lj, Cj])
```
