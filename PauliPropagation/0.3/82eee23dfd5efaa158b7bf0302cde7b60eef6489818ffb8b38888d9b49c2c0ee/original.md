```
setpauli(
    pstr::PauliStringType, 
    target_paulis::Vector{Symbol}, 
    qinds::Vector{Integer}
)
```

Set the Paulis `qinds` of an integer Pauli string `pstr` to `target_paulis`. `target_paulis` is a vector of symbols. Use tuples in performance critical functions because they are immutable.
