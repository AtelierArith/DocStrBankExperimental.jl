```
InterpretedSystem <: AbstractSystem
```

自動的に `F` とそのヤコビ行列の高速評価のためのプログラムを生成する [`AbstractSystem`](@ref) です。ただし、プログラムはコンパイルされず、解釈されます。 [`CompiledSystem`](@ref) も参照してください。

```
InterpretedSystem(F::System)
```

与えられた [`System`](@ref) `F` から `InterpretedSystem` を構築します。
