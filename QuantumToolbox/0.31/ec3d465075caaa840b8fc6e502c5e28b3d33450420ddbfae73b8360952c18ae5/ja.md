```
cosm(A::QuantumObject)
```

[`QuantumObject`](@ref) の行列コサインは次のように定義されます。

$$
\cos \left( \hat{A} \right) = \frac{e^{i \hat{A}} + e^{-i \hat{A}}}{2}
$$

この関数は `cos(A)` と同じであり、[`Operator`](@ref) と [`SuperOperator`](@ref) のみをサポートしています。
