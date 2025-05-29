```
groupby2(xs; keyfunc=identity, compare=isequal, emit=identity)
```

イテレータ `xs` からの要素のグループ `xg` を生成するイテレータであり、キーは `xs` の各要素に `keyfunc` を適用することによって計算されます。隣接するキーを `compare` 関数で比較し、その後、要素のグループのベクトル `xg` を出力します。

[documentation](https://hsugawa8651.github.io/GroupNumbers.jl/)を参照してください。
