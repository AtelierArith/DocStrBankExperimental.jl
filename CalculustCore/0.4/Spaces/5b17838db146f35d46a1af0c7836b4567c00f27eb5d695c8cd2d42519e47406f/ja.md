```
diffusionOp(ν::Number, V::AbstractSpace, discr::AbstractDiscretization)
```

拡散演算子: -νΔ

拡散係数 `ν` でスケーリングされた負のラプラス演算子を返します。`ν` は `SciMLOperators.ScalarOperator` と同じシグネチャを期待する `ν_update_func` によって更新できます。`ν` 以外のすべての位置引数は、負のラプラシアンを形成するために `laplaceOp` に渡されます。
