```
symboltoint(::TermType, paulis, qinds)
```

Maps a vector of symbols `paulis` acting on the indices `qinds` to an integer Pauli string with type `TermType`. Other sites are set to the identity. `qinds` can be any iterable.
