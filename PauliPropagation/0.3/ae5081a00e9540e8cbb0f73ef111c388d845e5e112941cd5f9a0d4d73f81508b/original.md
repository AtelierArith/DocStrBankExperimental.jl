```
symboltoint(nqubits::Integer, paulis::Vector{Symbol}, qinds::Vector{Int})
```

Maps a vector of symbols `pstr` acting on the indices `qinds` to an integer Pauli string. Other sites are set to the identity. `qinds` can be any iterable.
