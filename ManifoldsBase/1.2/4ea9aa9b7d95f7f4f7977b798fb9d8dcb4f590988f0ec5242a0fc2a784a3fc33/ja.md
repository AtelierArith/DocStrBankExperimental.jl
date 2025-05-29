```
InverseRetractionWithKeywords{R<:AbstractRetractionMethod,K} <: AbstractInverseRetractionMethod
```

逆リトラクションにはキーワードがある可能性があるため、この型はそれらを特定の逆リトラクションとして使用するための独自の型として設定する方法です。この型のもう一つの理由は、逆リトラクションに最初にディスパッチし、最後のレイヤーだけがキーワードで実装されるため、この方法でそれらを渡すことができるからです。

## フィールド

  * `inverse_retraction` キーワードで装飾された逆リトラクション
  * `kwargs` キーワード引数

この型はネストすることができることに注意してください。最も外側のキーワードの指定が使用されます。

## コンストラクタ

```
InverseRetractionWithKeywords(m::T; kwargs...) where {T <: AbstractInverseRetractionMethod}
```

キーワード `kwargs...` を持つために、サブタイプ `T <:`[`AbstractInverseRetractionMethod`](@ref) を指定します。
