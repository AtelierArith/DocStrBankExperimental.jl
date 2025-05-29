```
discretize(ahs::AnalogHamiltonianSimulation, device::Device)
```

新しい [`AnalogHamiltonianSimulation`](@ref) を作成し、すべての数値を `device` の能力に基づいて固定精度の `Dec128` オブジェクトとして表現します。
