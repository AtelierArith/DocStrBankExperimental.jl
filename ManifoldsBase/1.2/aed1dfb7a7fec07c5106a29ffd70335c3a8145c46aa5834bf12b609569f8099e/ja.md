```
RetractionWithKeywords{R<:AbstractRetractionMethod,K} <: AbstractRetractionMethod
```

リトラクションにはキーワードがある可能性があるため、このタイプはそれらを特定のリトラクションとして使用するための独自のタイプとして設定する方法です。このタイプのもう一つの理由は、リトラクションに対して最初にディスパッチし、最後のレイヤーだけがキーワードで実装されるため、この方法でそれらを下に渡すことができることです。

## フィールド

  * `retraction` キーワードで装飾されたリトラクション
  * `kwargs` キーワード引数

このタイプはネストすることができることに注意してください。最も外側のキーワードの指定が使用されます。

## コンストラクタ

```
RetractionWithKeywords(m::T; kwargs...) where {T <: AbstractRetractionMethod}
```

キーワード `kwargs...` を持つために、サブタイプ `T <:`[`AbstractRetractionMethod`](@ref) を指定します。
