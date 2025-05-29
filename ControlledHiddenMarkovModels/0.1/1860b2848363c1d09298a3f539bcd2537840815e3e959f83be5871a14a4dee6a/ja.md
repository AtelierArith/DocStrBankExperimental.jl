```
logdensityof(hmm::AbstractHMM, obs_sequence, par; safe)
```

`hmm`のパラメータ`par`に対する`obs_sequence`の対数尤度を計算します。

`safe = true`の場合、すべてが対数スケールで行われます。
