```
SciMLOperators.isconstant(A::AbstractQuantumObject)
```

[`AbstractQuantumObject`](@ref) `A`が時間的に定数であるかどうかをテストします。[`QuantumObject`](@ref)の場合、この関数は`true`を返しますが、[`QuantumObjectEvolution`](@ref)の場合、この関数は演算子が時間的に定数である場合に`true`を返します。
