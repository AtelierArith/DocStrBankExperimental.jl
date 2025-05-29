```
groupby2_dict(xs; keyfunc=identity, compare=isequal, emit=identity)
```

イテレータで、イテレータ `xs` からの要素のグループに対応するキー `(k,xg)` のペアを生成します。キー `k` は `xs` の各要素に `keyfunc` を適用することで計算されます。隣接するキーを `compare` 関数で比較し、その後、キー `k` と要素のグループのベクトル `xg` を出力します。

[ドキュメント](https://hsugawa8651.github.io/GroupNumbers.jl/)を参照してください。
