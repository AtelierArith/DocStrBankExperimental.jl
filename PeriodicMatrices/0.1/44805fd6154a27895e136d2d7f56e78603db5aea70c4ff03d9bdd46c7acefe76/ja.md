```
trace(A; rtol=sqrt(eps)) -> Atrace
```

連続時間周期行列の1周期にわたるトレースを計算します。連続時間周期行列 `A(t)` に対して、結果の `Atrace` は完全な周期にわたる点ごとのトレースの積分の平均値です。関与する時間積分は、相対誤差許容値 `rtol` を用いて適応的ガウス-クロンロッド数値積分によって評価されます。
