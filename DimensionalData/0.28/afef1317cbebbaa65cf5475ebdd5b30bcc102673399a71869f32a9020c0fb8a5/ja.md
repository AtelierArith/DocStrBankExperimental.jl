```
DimArray(f::Function, dim::Dimension; [name])
```

関数 `f` を次元 `dim` の値に対して適用し（`broadcast` を使用）、指定された次元を持つ次元配列として結果を返します。結果の名前をオプションで提供できます。
