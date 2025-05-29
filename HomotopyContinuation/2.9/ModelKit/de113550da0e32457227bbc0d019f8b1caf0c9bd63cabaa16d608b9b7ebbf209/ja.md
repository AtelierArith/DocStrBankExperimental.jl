```
InterpretedHomotopy <: AbstractHomotopy
```

自動的に `H` とそのヤコビ行列の高速評価のためのプログラムを生成する [`AbstractHomotopy`](@ref) です。ただし、プログラムはコンパイルされず、解釈されます。 [`CompiledHomotopy`](@ref) も参照してください。

```
InterpretedHomotopy(H::Homotopy)
```

与えられた [`Homotopy`](@ref) `H` から `InterpretedHomotopy` を構築します。
