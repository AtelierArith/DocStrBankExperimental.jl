```
sinm(A::QuantumObject)
```

[`QuantumObject`](@ref) の行列サインは次のように定義されます。

$$
\sin \left( \hat{A} \right) = \frac{e^{i \hat{A}} - e^{-i \hat{A}}}{2 i}
$$

この関数は `sin(A)` と同じであり、[`Operator`](@ref) と [`SuperOperator`](@ref) のみをサポートしています。
