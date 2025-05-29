可引用ノード `cn` を指定された正字法システムのトークナイザーを使用してトークン化します。

```julia
tokenize(psg, ortho; edition, exemplar)

```

返される値は、`CitablePassage` とトークンカテゴリのペアのリストです。可引用ノードはトークンのレベルで可引用です。
