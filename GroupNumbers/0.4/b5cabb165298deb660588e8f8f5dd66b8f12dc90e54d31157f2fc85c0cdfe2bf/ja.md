```
groupby_numbers_indices(xs; keyfunc=identity, kwargs)
```

数値のイテレータ `xs` からインデックスのグループ `ig` を生成するイテレータであり、キーは `xs` の各要素に `keyfunc` を適用することによって計算されます。隣接するキーを `isapprox` 関数を用いて、提供された `kwargs` のオプションパラメータで比較し、その後、インデックスのグループのベクトル `ig` を出力します。

[documentation](https://hsugawa8651.github.io/GroupNumbers.jl/) を参照してください。
