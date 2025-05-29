```
CliffordGate(symbol::Symbol, qinds::Vector{Int})
CliffordGate(symbol::Symbol, qinds::Int)
```

A Clifford gate with the name `symbol` acting on the qubits `qinds`. `symbol` needs to match any of the implemented Clifford gates in the global `clifford_map`. `qinds` can be a single integer, a vector of integers, or anything that transforms into a vector via `vec(collect(qinds))`.
