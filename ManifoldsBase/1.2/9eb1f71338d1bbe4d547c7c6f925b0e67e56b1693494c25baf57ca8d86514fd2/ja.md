EmbeddedInverseRetraction{T<:AbstractInverseRetractionMethod} <: AbstractInverseRetractionMethod

逆リトラクションを計算するには、埋め込み内でタイプ `T` の逆リトラクションを使用し、結果を投影します。

# コンストラクタ

```
EmbeddedInverseRetraction(r::AbstractInverseRetractionMethod)
```

埋め込みで使用する逆リトラクション `r` を持つ逆リトラクションを生成します。
