```
is_strict_subset_tn(a::ThickNumber, b::ThickNumber)
⪽(a::ThickNumber, b::ThickNumber)
```

`a`が`b`の厳密な部分集合である場合は`true`を返し、そうでない場合は`false`を返します。`a`が`b`の厳密な部分集合であるとは、`a`が`b`の部分集合であり、`b`と等しくない場合です。

これは単に`⊂`ではない理由については、ドキュメントを参照してください。
