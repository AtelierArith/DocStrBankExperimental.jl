```
SciMLOperators.cached_operator(L::AbstractQuantumObject, u)
```

`u`-のような入力ベクトルを用いたインプレース評価のために、[`AbstractQuantumObject`](@ref) `L` のキャッシュを割り当てます。

ここで、`u` は以下のいずれかの型であることができます：

  * `AbstractVector`
  * [`Ket`](@ref)型の[`QuantumObject`](@ref)（`L`が[`Operator`](@ref）の場合）
  * [`OperatorKet`](@ref)型の[`QuantumObject`](@ref)（`L`が[`SuperOperator`](@ref）の場合）
