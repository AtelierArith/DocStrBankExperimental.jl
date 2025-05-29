```
Cascade(components::Vector{CircuitComponent},
    operations::Vector{Pair{PortOperation, Vector{String}}})
```

複数のCircuitComponentをカスケードして統合し、その後ポートにPortOperationsを適用することによって作成されたシステムです。
