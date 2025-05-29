```
reflect(kernel) --> reflectedkernel
```

カーネル `kernel` の周りの点ごとの反射を 0, 0, ... で計算します。`reflectedkernel` を使用して `imfilter` を使用すると、元の `kernel` に関して畳み込みではなく相関を実行します。
