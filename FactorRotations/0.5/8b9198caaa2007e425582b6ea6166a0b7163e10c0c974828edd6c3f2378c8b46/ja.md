```
RotationMethod{T<:RotationType}
```

因子回転法を表す抽象型です。

`M <: RotationMethod` の各実装は、[`criterion_and_gradient!`](@ref) メソッドを提供しなければなりません。
