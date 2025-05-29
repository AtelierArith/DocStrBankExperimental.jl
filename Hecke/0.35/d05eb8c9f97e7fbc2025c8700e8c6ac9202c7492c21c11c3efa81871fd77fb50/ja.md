```
signs(a::NumFieldElem, [embs::Vector{NumFieldEmb} = real_embeddings(K)])
                                                   -> Dict{NumFieldEmb, Int}
```

`a`の実埋め込み`embs`における符号を辞書として返します。デフォルトでは、数体のすべての実埋め込みが使用されます。

# 例

```jldoctest; filter = r"Complex.*"
julia> K, a = quadratic_field(3);

julia> signs(a)
Dict{AbsSimpleNumFieldEmbedding, Int64} with 2 entries:
  Complex embedding corresponding to -1.73 of real quadratic field define… => -1
  Complex embedding corresponding to 1.73 of real quadratic field defined… => 1
```
