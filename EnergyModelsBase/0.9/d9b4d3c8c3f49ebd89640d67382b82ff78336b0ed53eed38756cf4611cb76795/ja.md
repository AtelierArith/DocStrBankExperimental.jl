```
AbstractInvestmentModel <: EnergyModel
```

抽象投資モデルタイプ。

この抽象モデルタイプは、投資を利用する追加の [`EnergyModel`](@ref) タイプを作成する際に使用されるべきです。

!!! note
    `EnergyModelsBase` 内で宣言されているにもかかわらず、その具体的なものは `EnergyModelsInvestments` がロードされている場合にのみアクセス可能です。


追加のタイプの例として、*e.g.*, `SDDP` の含有が挙げられます。
