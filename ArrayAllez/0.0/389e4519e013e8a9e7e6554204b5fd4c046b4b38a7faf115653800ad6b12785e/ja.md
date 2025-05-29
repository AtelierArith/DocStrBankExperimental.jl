```
log!(A)
log_(A) ≈ log!(similar(A), A)
log0(A) = log.(A)
```

要素ごとのインプレース自然対数、およびその仲間。`length(A) >= 5000` の場合はマルチスレッドで処理されます。これらのうちの1つをロードすると、`Yeppp`、`AppleAccelerate`、または `IntelVectorMath` によって処理されます。
