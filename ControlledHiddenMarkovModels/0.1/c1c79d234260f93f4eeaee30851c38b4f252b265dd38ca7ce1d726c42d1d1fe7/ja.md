```
infer_current_state(hmm::AbstractHMM, obs_sequence, par; safe)
```

`par`を持つ`hmm`に対して`obs_sequence`が与えられたときの現在の状態の事後分布を推定します。

`safe = true`の場合、すべてが対数スケールで行われます。
