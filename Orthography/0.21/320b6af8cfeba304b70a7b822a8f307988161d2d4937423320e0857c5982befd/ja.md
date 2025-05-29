コーパス `c` を指定された正字法システムのトークナイザーを使用してトークン化します。

```julia
tokenize(c, ortho; edition, exemplar)

```

返り値は、`CitablePassage` とトークンカテゴリのペアのリストです。引用可能なノードはトークンのレベルで引用可能です。
