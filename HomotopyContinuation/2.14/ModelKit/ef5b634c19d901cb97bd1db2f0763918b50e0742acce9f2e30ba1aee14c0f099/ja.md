```
CompiledHomotopy <: AbstractHomotopy
```

自動的にホモトピー `H` とそのヤコビ行列の高速評価のための直線プログラムをコンパイルする [`AbstractHomotopy`](@ref) です。大きなホモトピーの場合、コンパイルには時間がかかり、大量のメモリを必要とすることがあります。これが問題であれば、[`InterpretedHomotopy`](@ref) を検討してください。

```
CompiledSystem(F::System)
```

与えられた [`System`](@ref) `F` から `CompiledSystem` を構築します。
