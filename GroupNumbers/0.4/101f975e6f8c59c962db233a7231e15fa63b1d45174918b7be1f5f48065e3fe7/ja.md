```
groupby_numbers_dict_indices(xs; keyfunc=identity, kwargs)
```

数値のイテレータ `xs` から、キーと対応するインデックスのグループのペア `(k,ig)` を生成するイテレータです。キー `k` は `xs` の各要素に `keyfunc` を適用することで計算されます。隣接するキーを、提供された `kwargs` のオプションパラメータを使って `isapprox` 関数で比較し、その後、キー `k` とインデックスのグループのベクトル `ig` を出力します。

[documentation](https://hsugawa8651.github.io/GroupNumbers.jl/) を参照してください。
