```
SuptBand(nuncovered::Real=0; ndraw::Real=1_000_000)
```

`ndraw` のランダム数を計算に必要とする `SuptBand` インスタンスを返します。結果は、`ndraw` の値が大きいほどより正確になる傾向があります。

`nuncovered` の正の値は、Montiel Olea と Plagborg-Møller (2019) によって説明された一般化された誤差率制御を可能にします。具体的には、カバレッジを考慮する際に、最大で `nuncovered` 個の点推定値が信頼区間にカバーされていないことが許可されます。

# 参考文献

  * Montiel Olea, José Luis and Mikkel Plagborg-Møller. 2019. "Simultaneous Confidence Bands: Theory, Implementation, and an Application to SVARs." Journal of Applied Econometrics 34 (1): 1-17.
