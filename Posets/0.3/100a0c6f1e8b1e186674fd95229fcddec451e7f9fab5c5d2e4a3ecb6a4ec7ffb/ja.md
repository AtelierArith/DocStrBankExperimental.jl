```
are_incomparable(p::Poset, a::Integer, b::Integer)::Bool
```

`a` と `b` が `p` に含まれ、かつ次のいずれも真でない場合に `true` を返します: `a<b` または `a==b` または `b<a`。
