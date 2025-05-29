```
productstate(N::Int, states::Vector{T})
productstate(hilbert::Vector{<:Index}, states::Vector{T})
```

Generate an MPS wavefunction for a given input product state `states`. The state `T` can be specified either with bit values $|\psi\rangle = |1\rangle\otimes|0\rangle\otimes|1\rangle$

```julia
ψ = productstate(q, [1,0,1])
# MPS
# [1] ((dim=2|id=717|"Qubit,Site,n=1"),)
# [2] ((dim=2|id=89|"Qubit,Site,n=2"),)
# [3] ((dim=2|id=895|"Qubit,Site,n=3"),)
```

or with `String` $|\psi\rangle = |+\rangle\otimes|0\rangle\otimes|-i\rangle$

```julia
ψ = productstate(q, ["X+","Z+","Y-"]);
```
