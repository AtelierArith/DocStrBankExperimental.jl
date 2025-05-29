```
createcliffordmap(gate_relations::Dict)
```

Create a Clifford gate map from a dictionary of gate relations which can then be pushed to the global `clifford_map`. `gate_relations` is a dictionary with pairs like `(:X, :X) => (:Z, :X, -1)`, describing the action of the Clifford gate on symbols (including the sign change).
