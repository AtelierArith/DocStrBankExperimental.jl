```julia
kron(A, B)

```

`A ⊗ B`のクロンケル積の遅延表現を構築します。2つの因子のうちの1つは`AbstractMatrix`である必要があり、その場合は自動的に`MatrixOperator`に昇格されます。一般的な[`Base.kron`](@ref)へのフォールバックを避けるために、`A`または`B`の少なくとも1つは`AbstractSciMLOperator`でなければなりません。
