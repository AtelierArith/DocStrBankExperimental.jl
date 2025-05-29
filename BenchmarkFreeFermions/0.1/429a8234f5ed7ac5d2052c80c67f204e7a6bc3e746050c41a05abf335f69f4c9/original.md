```
 ExpectationValue(G::Matrix{F},
      si::Vector{Int64},
      dagidx::Vector{Int64}) -> ::F
```

Return the expectation value of severial fermionic operators. `si` denotes the sites and `dagidx` tells whether the operator is daggered or not. For example, `si = [i, j]` and `dagidx = [2]` means the single particle correlation `c_i c_j^dag` and `si = [i, j, k, l]` and `dagidx = [3, 4]` means the pairing correlation `c_i c_j c_k^dag c_l^dag`. 
