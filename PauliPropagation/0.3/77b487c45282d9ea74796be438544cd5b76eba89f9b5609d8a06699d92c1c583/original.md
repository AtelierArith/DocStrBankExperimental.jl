```
setpauli(
    pstr::PauliStringType, 
    target_paulis::PauliStringType, 
    qinds::Vector{Integer}
)
```

Set the Paulis `qinds` of an integer Pauli string `pstr` to `target_paulis`. Use Tuples for `qinds` in performance critical functions because they are immutable.
