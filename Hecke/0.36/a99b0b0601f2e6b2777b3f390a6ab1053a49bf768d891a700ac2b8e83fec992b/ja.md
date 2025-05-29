```
primitive_closure(M::AbstractLat, N::AbstractLat) -> AbstractLat
```

数体 `E` 上で定義された二つのラティス `M` と `N` が与えられ、$N \subseteq E\otimes M$ の場合、`M` における `N` の原始閉包 $M \cap E\otimes N$ を返します。

別名 `saturate(L, M)` を使用することもできます。
