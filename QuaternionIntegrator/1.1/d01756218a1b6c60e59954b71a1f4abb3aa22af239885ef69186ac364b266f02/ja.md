```
integrate(q0::Quaternion, ω0::Vector, Ib::Matrix, ∆t, torque::Function, N::Integer)
```

`N` タイムステップ先の回転状態を統合します。

`(q1, ω1)` を返します。これは、`N` 回の統合ステップ後の向きと角速度です。
