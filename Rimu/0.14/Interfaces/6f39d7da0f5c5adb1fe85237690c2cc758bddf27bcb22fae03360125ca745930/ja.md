```
LinearAlgebra.mul!(w::AbstractDVec, op::AbstractOperator, v::AbstractDVec)
```

`op`と`v`のインプレース乗算を行い、結果を`w`に格納します。結果が返されます。`w`は`eltype(op)`と`valtype(v)`のインスタンスの積を保持できる`valtype`を持つ必要があります。さらに、`w`の[`StochasticStyle`](@ref)は[`<:IsDeterministic`](@ref Rimu.StochasticStyles.IsDeterministic)である必要があります。

[`AbstractOperator`](@ref)インターフェースの一部です。

デフォルトの実装は、演算子の要素にアクセスするために[`diagonal_element`](@ref)と[`offdiagonals`](@ref)に依存しています。この関数はカスタム演算子のためにオーバーロードできます。
