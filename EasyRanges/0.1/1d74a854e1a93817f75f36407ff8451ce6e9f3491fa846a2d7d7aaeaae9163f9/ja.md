```
EasyRanges.shrink(a, b)
```

は、`a` を `b` の量だけ縮小する結果を返します。これは、[`@range`](@ref) マクロにおける式 `a ∓ b` と同等です。

外部パッケージは、特定の `a` と `b` の型に対して `EasyRanges.shrink(a, b)` を拡張することがあります。
