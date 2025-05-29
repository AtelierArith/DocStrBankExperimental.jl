```
exp!(A)
exp_(A) = exp!(similar(A), A)
exp0(A) ≈ exp.(A)
```

要素ごとのインプレース指数関数とその仲間。`length(A) >= 5000` の場合はマルチスレッドで処理されます。これらのうちの1つをロードすると、`Yeppp` または `AppleAccelerate` または `IntelVectorMath` によって処理されますが、`Yeppp` は遅くなる可能性があります。
