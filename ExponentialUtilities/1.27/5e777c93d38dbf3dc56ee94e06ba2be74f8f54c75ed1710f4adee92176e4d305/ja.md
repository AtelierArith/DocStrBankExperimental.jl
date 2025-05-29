```
expv!(w, t, A, b, Ks, cache)
```

ベクトル `b` に対する `exp(t*A)` の作用を計算し、その結果を `w` に格納するための代替インターフェースです。生成された部分空間における行列指数関数の誤差推定が要求された許容誤差を下回ると、Krylov 反復は終了します。`Ks` は `KrylovSubspace` であり、`typeof(cache)<:HermitianSubspaceCache` で、正確な型が部分空間指数を計算するために使用されるアルゴリズムを決定します。
