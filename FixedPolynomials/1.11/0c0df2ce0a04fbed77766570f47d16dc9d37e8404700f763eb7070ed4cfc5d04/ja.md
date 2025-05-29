```
weyldot(f::Polynomial, g::Polynomial)
```

[バンビエリ-ウェイリ点積](https://en.wikipedia.org/wiki/Bombieri_norm)を計算します。`f`と`g`が同次である場合にのみ、これは正しく定義されます。

```
weyldot(f::Vector{Polynomial}, g::Vector{Polynomial})
```

多項式のベクトルに対して点積を計算します。
