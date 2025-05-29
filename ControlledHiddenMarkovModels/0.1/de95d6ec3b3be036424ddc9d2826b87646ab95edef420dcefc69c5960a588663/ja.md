```
infer_current_state(
    hmm::AbstractControlledHMM, obs_sequence, control_sequence, par; safe
)
```

`obs_sequence` に対して `hmm` の現在の状態の事後分布を、制御 `control_sequence` とパラメータ `par` を用いて推定します。

`safe = true` の場合、すべてが対数スケールで行われます。
