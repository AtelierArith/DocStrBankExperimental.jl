```
subsample_random(X::AbstractAlignment, m::Int)
```

`X`からランダムに`m`シーケンスを取得した`Alignment`を返します。サンプリングは重複なしで行われるため、`m`シーケンスはすべて`X`の異なる位置にあります。
