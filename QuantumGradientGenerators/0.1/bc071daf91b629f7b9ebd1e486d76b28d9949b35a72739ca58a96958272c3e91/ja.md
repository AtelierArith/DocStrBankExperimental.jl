与えられた勾配ベクトルを新しい勾配評価のためにリセットします。

```julia
resetgradvec!(Ψ̃::GradVector)
```

`Ψ̃.grad_states`をゼロにしますが、`Ψ̃.state`には影響を与えません。これは、Ψ̃がインプレース操作をサポートしているかどうかに関係なく可能です（[`QuantumPropagators.Interfaces.supports_inplace`](@ref)）。

```julia
resetgradvec!(Ψ̃::GradVector, Ψ)
```

さらに、`Ψ̃.state`を`Ψ`に設定します。これは、`Ψ̃.state`がインプレース操作をサポートしている必要があります。

`Ψ̃`を返します。
