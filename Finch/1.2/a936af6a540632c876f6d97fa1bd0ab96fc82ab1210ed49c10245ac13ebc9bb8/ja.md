```
Tensor(lvl, [undef], dims...)
```

サイズ `dims` の `Tensor` を構築し、`undef` で初期化し、必要に応じてメモリを割り当てます。ここで `undef` は `UndefInitializer` シングルトン型です。`dims...` は可変数の次元または次元のタプルである可能性がありますが、`lvl` の次元数に対応している必要があります。
