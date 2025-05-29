```julia
AddVector(b; update_func, update_func!, accepted_kwargs)

```

アフィン演算 `w = I * v + I * b` を表します。更新関数 `update_func[!]` は `AbstractVecOrMat` `b` の状態を更新します。詳細については `AffineOperator` のドキュメントを参照してください。
