```
POS(tree)
```

品詞タグ付き単語のためのイテレータ。

```jldoctest
julia> POS(tree"(S (NP (DT the) (N cat)) (VP (V ate)))") |> collect
3-element Array{Any,1}:
 ("DT", "the")
 ("N", "cat")
 ("V", "ate")
```

# 引数

  * `tree`: 検索する木

# 戻り値

  * `POSIterator` - (POS, トークン) ペアの遅延イテレータ
