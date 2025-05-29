```
isunitary(U::QuantumObject; kwargs...)
```

[`QuantumObject`](@ref) $U$ がユニタリ演算子であるかどうかをテストします。この関数は `Base.isapprox` を呼び出して、$U U^\dagger$ が単位演算子に近いかどうかをテストします。

すべてのキーワード引数は `Base.isapprox` に渡されることに注意してください。
