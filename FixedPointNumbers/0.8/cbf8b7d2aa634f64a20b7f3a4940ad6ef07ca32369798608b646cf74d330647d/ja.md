```
sd, ad = scaledual(s::Number, a)
```

`sd` と `ad` を返します。ここで `sd * ad == s * a` です。`a` が FixedPoint 数の配列である場合、`sd*ad` の計算は `s*a` よりも速いかもしれません。
