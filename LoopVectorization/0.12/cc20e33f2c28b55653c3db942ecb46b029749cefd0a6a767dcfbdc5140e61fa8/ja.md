```
vsum(A::DenseArray)
vsum(f, A::DenseArray)
```

`sum`のベクトル化バージョン。最初の引数として関数を提供すると、合計する前にその関数が`A`の各要素に適用されます。
