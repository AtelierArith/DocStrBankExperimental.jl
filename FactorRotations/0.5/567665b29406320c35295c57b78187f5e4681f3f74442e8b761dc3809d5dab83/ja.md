```
criterion(method::RotationMethod, Λ::Abstractmatrix{<:Real})
```

与えられた `method` に対する基準を因子負荷行列 `Λ` に関して計算します。

このメソッドは、[`criterion_and_gradient!(nothing, method, Λ)`](@ref criterion_and_gradient!) 呼び出しのラッパーに過ぎません。
