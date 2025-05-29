```
MinMaxSimplification(method; min=3, max=typemax(Int), maxiter=10)
```

バイナリサーチアルゴリズムと親の簡略化 `method` を使用してジオメトリを簡略化します。

簡略化は、頂点の数が `[min, max]` の範囲内になるか、最大反復回数 `maxiter` に達するまで行われます。
