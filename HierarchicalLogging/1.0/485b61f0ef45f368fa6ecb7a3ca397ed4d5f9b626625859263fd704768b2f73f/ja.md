```
HierarchicalLogger{T<:AbstractLogger} <: AbstractLogger
```

`AbstractLogger`は、次の形式の名前を持つタイプ`T`の1つ以上の子ロガーで構成されています。

```julia
    key₁.key₂.key₃. ... .keyₙ
```

`H::HierarchicalLogger`が与えられたとき、ラベル`key₁.key₂. ... .keyⱼ`を持つロガー`L`の親は、`L`と最も長い接頭辞を共有するロガー`P ∈ H`です。すなわち、`P`のラベルは`key₁.key₂. ... .keyᵢ`であり、`i < j`が`H`内で最大です。

このコレクションには、常に空のラベルを持つルートのロガーが含まれています。
