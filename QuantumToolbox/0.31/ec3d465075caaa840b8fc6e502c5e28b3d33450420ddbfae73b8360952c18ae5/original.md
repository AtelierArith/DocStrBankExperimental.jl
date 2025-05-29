```
cosm(A::QuantumObject)
```

Matrix cosine of [`QuantumObject`](@ref), defined as

$\cos \left( \hat{A} \right) = \frac{e^{i \hat{A}} + e^{-i \hat{A}}}{2}$

Note that this function is same as `cos(A)` and only supports for [`Operator`](@ref) and [`SuperOperator`](@ref).
