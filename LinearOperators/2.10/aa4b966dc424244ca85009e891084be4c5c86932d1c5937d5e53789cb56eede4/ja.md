```
LinearOperator(M::SymTridiagonal{T}, S = Vector{T}) where {T}
```

対称トリディアゴナル行列から線形演算子を構築します。要素が実数の場合、エルミート行列でもあり、そうでない場合は複素対称行列です。`S`を使用してGPU上のLinearOperatorsに変更します。
