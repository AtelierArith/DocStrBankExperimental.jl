```
groupby_numbers_dict(xs; keyfunc=identity, emit=identity, kwargs)
```

イテレータで、キーとイテレータ `xs` からの対応する要素のグループのペア `(k,xg)` を生成します。ここで、キー `k` は `xs` の各要素に `keyfunc` を適用することによって計算されます。隣接するキーを、提供された `kwargs` オプションパラメータを使って `isapprox` 関数で比較し、その後、キー `k` と要素のグループのベクトル `xg` を出力します。

[documentation](https://hsugawa8651.github.io/GroupNumbers.jl/) を参照してください。
