```
get_y(x, algorithm = "nn")
```

データベクトル `x` に対応するコンテキストベクトル `y` を返します。いくつかのタイプのコンテキストが可能で、`type` 引数によって選択されます。type = "nn" は `x` の各点の次の近傍を指します。type = "an" は "隣接近傍" を意味し、`x` の各要素の前後の要素を指します。
