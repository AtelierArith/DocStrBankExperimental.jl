```
logdensityof(hmm::AbstractControlledHMM, obs_sequence, control_sequence, par; safe)
```

`hmm`の`obs_sequence`の対数尤度を`control_sequence`と`par`の制御で計算します。

`safe = true`の場合、すべてが対数スケールで行われます。
