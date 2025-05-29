```
Node(instanceof, children...; props...)
Node(instanceof, children, props)
```

WebIOの基本構成要素。`Node`は単に*インスタンス*（いくつかのJuliaオブジェクト）といくつかの子ノードおよび追加のプロパティをラップするものです。

最も一般的なタイプの`Node`はDOMノードです。これらは、`instanceof`としてシンボルを指定するだけで構築できます（内部的には`WebIO.DOM`のインスタンスに昇格されます）。

```jldoctest
julia> Node(:div, Node(:p, "私は段落です！", class="important"))
(div
  (p { class="important" }
    "私は段落です！"))
```

カスタム（非`DOM`）インスタンスを持つノードには、対応する`WebIO.render`メソッドが定義されている必要があります。
