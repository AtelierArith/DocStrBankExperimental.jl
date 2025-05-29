```
ispauli(pauli1::Union{Symbol, PauliType}, pauli2::Union{Symbol, PauliType})

ispauli(pauli1::Union{Vector{Symbol}, PauliStringType}, pauli2::Union{Vector{Symbol}, PauliStringType})
```

Check if two Paulis are equal, where one is given as a symbol and the other as an integer.
