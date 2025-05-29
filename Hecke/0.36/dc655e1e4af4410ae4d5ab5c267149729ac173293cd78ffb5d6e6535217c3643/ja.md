```
signs(a::NumFieldElem, [embs::Vector{NumFieldEmb} = real_embeddings(K)])
                                                   -> Dict{NumFieldEmb, Int}
```

`a`の実埋め込み`embs`における符号を辞書として返します。デフォルトでは、数体のすべての実埋め込みが使用されます。

# 例

```jldoctest; filter = r"Real.*"
julia> K, a = quadratic_field(3);

julia> signs(a)
Dict{AbsSimpleNumFieldEmbedding, Int64} with 2 entries:
  Real embedding with -1.73 of K => -1
  Real embedding with 1.73 of K  => 1
```
