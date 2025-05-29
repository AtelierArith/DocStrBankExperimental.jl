```
variance(O::QuantumObject, ψ::Union{QuantumObject,Vector{QuantumObject}})
```

[`Operator`](@ref) `O` の分散: $\langle\hat{O}^2\rangle - \langle\hat{O}\rangle^2$、

ここで、$\langle\hat{O}\rangle$ は状態 `ψ` に対する `O` の期待値です（[`expect`](@ref) も参照）。状態 `ψ` は [`Ket`](@ref)、[`Bra`](@ref)、または [`Operator`](@ref) であることができます。

この関数は、`O` がエルミートの場合は実数を返し、そうでない場合は複素数を返します。

`ψ` は [`QuantumObject`](@ref) のリストとしても与えることができ、その場合は期待値のリストを返します。
