```
getADO(ados, idx)
```

Return the auxiliary density operator with a specific index from auxiliary density operators

This function equals to calling : `ados[idx]`.

# Parameters

  * `ados::ADOs` : the auxiliary density operators for HEOM model
  * `idx::Int` : the index of the auxiliary density operator

# Returns

  * `ρ_idx::QuantumObject` : The auxiliary density operator
