```
mpo = makeqMPO(Qlabels,mpo)
```

Generates quantum number MPO from a dense Hamiltonian based on `Qlabels`

# Arguments:

  * `mpo::MPO`: dense MPO
  * `Qlabels::Array{Array{Qnum,1},1}`: quantum numbers for physical indices (modulus size of vector)
