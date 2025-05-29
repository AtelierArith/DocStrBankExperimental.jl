```
planar_symmetric_qubit_povm( n :: Int64 ) :: POVM{Float64}
```

[`planar_symmetric_qubit_states`](@ref) から `n` 要素の `POVM{Float64}` を構築します。各状態は完全性関係を満たすために `2/n` の係数で乗算されます。

`n ≥ 2` が満たされない場合、`DomainError` がスローされます。
