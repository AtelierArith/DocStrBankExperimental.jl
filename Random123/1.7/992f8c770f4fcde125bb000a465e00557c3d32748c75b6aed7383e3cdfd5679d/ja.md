```julia
AESNI4x <: AbstractAESNI4x
AESNI4x([seed])
```

AESNI4xはAESNIカウンタベースのRNGの一種です。一度に4つの`UInt32`数を生成します。

`seed`は4つの`Integer`の`Tuple`で、すべて自動的に`UInt32`に変換されます。

[`R123_USE_AESNI`](@ref)が有効な場合のみ使用可能です。
