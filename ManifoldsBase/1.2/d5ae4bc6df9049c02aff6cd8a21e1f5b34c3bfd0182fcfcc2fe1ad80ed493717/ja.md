```
VectorTransportWithKeywords{V<:AbstractVectorTransportMethod, K} <: AbstractVectorTransportMethod
```

ベクトル輸送にはキーワードがある可能性があるため、この型はそれらを特定のベクトル輸送として使用するための独自の型として設定する方法です。この型のもう一つの理由は、最初にベクトル輸送にディスパッチし、最後のレイヤーだけがキーワードで実装されるため、この方法でそれらを渡すことができることです。

## フィールド

  * `vector_transport` キーワードで装飾されたベクトル輸送
  * `kwargs` キーワード引数

この型はネストすることができることに注意してください。最も外側のキーワードの指定が使用されます。

## コンストラクタ

```
VectorTransportWithKeywords(m::T; kwargs...) where {T <: AbstractVectorTransportMethod}
```

キーワード `kwargs...` を持つために、サブタイプ `T <:`[`AbstractVectorTransportMethod`](@ref) を指定します。
