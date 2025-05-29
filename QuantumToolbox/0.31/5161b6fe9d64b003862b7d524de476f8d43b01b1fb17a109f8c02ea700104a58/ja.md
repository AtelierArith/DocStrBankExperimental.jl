```
(A::QuantumObjectEvolution)(ψ, p, t)
```

時間依存の [`QuantumObjectEvolution`](@ref) オブジェクト `A` を、入力状態 `ψ` に時間 `t` でパラメータ `p` を使って適用します。出力状態は新しい [`QuantumObject`](@ref) オブジェクトに保存されます。この関数は `AbstractSciMLOperator` オブジェクトの動作を模倣します。
