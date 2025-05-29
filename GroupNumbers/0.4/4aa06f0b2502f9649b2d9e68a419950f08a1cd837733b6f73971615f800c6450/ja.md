```
groupby_numbers(xs; keyfunc=identity, emit=identity, kwargs)
```

数値のイテレータ `xs` からグループ `xg` を生成するイテレータで、キーは `xs` の各要素に `keyfunc` を適用することによって計算されます。隣接するキーを `isapprox` 関数を用いて、提供された `kwargs` のオプションパラメータで比較し、その後、数値のグループのベクトル `xg` を出力します。

[documentation](https://hsugawa8651.github.io/GroupNumbers.jl/) を参照してください。
