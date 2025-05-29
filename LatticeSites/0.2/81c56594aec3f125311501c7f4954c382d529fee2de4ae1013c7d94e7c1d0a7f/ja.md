```
randflip!(config) -> (proposed_index, config)
randflip!(::FlipStyle, config) -> (proposed_index, config)
```

与えられたフリップスタイルを使用して格子構成をランダムに反転させます。デフォルトのフリップスタイルは [`UniformFlip`](@ref){1} で、これは構成内の **1** つのサイトを均等に選択して反転させます。

常に `config[proposed_index]` を使用してこの格子構成の現在の値を取得できるはずです。サイトを変更できるかどうかは、構成が可変型に格納されているかどうかに依存します。
