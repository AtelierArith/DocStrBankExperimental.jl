```
Words(tree)
```

文中の単語のイテレータ。

```jldoctest
julia> Words(tree"(S (NP (DT the) (N cat)) (VP (V ate)))") |> collect
3-element Array{Any,1}:
 "the"
 "cat"
 "ate"
```

# 引数

  * `tree`: 検索する木

# 戻り値

  * `WordsIterator`: トークンのイテレータ
