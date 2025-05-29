```
groupby2_dict_indices(xs; keyfunc=identity, compare=isequal)
```

イテレータで、イテレータ `xs` からのインデックスのグループに対応するキーとペア `(k,ig)` を生成します。キー `k` は `xs` の各要素に `keyfunc` を適用することによって計算されます。隣接するキーを `compare` 関数で比較し、その後、キー `k` とインデックスのグループのベクトル `ig` を出力します。

[documentation](https://hsugawa8651.github.io/GroupNumbers.jl/) を参照してください。
