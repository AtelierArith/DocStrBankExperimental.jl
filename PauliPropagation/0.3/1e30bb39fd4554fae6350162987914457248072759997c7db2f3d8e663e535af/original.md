```
TransferMapGate(transfer_map::Vector{Vector{Tuple{TermType,CoeffType}}}, qinds::Vector{Int})
```

A non-parametrized `StaticGate` defined by a transfer map acting on the qubits `qinds`. Transfer maps can be constructed manually or generated via `totransfermap()`.
