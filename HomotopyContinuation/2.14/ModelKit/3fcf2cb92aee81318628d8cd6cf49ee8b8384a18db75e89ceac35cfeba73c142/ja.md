```
CompiledSystem <: AbstractSystem
```

自動的にシステム `F` とそのヤコビアンの高速評価のための直線プログラムをコンパイルする [`AbstractSystem`](@ref) です。大規模なシステムの場合、コンパイルには時間がかかり、大量のメモリを必要とすることがあります。これが問題であれば、[`InterpretedSystem`](@ref) を検討してください。

```
CompiledSystem(F::System)
```

与えられた [`System`](@ref) `F` から `CompiledSystem` を構築します。
