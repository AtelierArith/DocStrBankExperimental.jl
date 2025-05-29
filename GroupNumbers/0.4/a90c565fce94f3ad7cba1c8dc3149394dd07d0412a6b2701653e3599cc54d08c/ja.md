```
groupby2_indices(xs; keyfunc=identity, compare=isequal)
```

イテレータ `xs` からインデックスのグループ `ig` を生成するイテレータで、キーは `xs` の各要素に `keyfunc` を適用することで計算されます。隣接するキーを `compare` 関数で比較し、その後、インデックスのグループのベクトル `ig` を出力します。

[documentation](https://hsugawa8651.github.io/GroupNumbers.jl/) を参照してください。
