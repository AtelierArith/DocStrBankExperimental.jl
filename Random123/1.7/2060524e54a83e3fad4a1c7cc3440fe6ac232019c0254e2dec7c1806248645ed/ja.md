```julia
AESNI1x <: AbstractAESNI1x
AESNI1x([seed])
```

AESNI1xはAESNIカウンターベースのRNGの一種です。一度に1つの`UInt128`数を生成します。

`seed`は`Integer`で、自動的に`UInt128`に変換されます。

[`R123_USE_AESNI`](@ref)が有効な場合のみ使用可能です。
