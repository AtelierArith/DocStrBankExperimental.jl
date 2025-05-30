```
StateVectorSimulator([::T], qubit_count::Int, shots::Int) -> StateVectorSimulator{T, Vector{T}}
```

`2^qubit_count` 要素と測定する `shots` ショットを持つ `StateVectorSimulator` を作成します。デフォルトの要素型は `ComplexF64` です。
