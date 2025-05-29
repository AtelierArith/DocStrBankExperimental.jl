```
mm(i, j:k, ...)
mm(pattern)
```

最初の形式は、整数および整数範囲の引数を持ち、Matrix Market コレクション内の ID 番号によって選択されるパターンです。

2 番目の形式は、パターンであり、名前によってパターンに対応する Matrix Market コレクション内の行列を選択します。たとえその名前が Suite Sparse コレクションからのものであってもです。

例:     mdlist(mm("*/1138*bus")) == ["Harwell-Boeing/psadmit/1138*bus"]
