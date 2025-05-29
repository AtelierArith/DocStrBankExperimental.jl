```
sinm(A::QuantumObject)
```

Matrix sine of [`QuantumObject`](@ref), defined as

$\sin \left( \hat{A} \right) = \frac{e^{i \hat{A}} - e^{-i \hat{A}}}{2 i}$

Note that this function is same as `sin(A)` and only supports for [`Operator`](@ref) and [`SuperOperator`](@ref).
