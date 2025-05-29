```
rem_relation!(p::Poset, a::Integer, b::Integer)::Bool
```

ポセット `p` から関係 `a < b` を削除し、さらに `a` と `b` の間にある `x` に対して `a < x` および `x < b` の形のすべての関係を削除します。
