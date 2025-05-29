```julia
domain_kind(x)

```

ドメインタイプ（推奨）または値の*種類*を返します。ドメインでないオブジェクト/タイプに対してはエラーが発生します。変換のドメインにも対応しています。

以下の返り値が可能です：

1. `:univariate`、その境界は `minimum`、`maximum`、および `extrema` を使用してアクセスできます。
2. `:multivariate`、これは `length`、`getindex` (`[]`)、および `Tuple` への変換をサポートします。
