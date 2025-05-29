```
tfer = match_transfer_patch_times(startorb, endorb, stime, etime, patch_posns; atol=1e-6, maxit=100)
tfer = match_transfer_patch_times(tfer; kwargs...)
```

パッチの両側でパッチ時間が連続するように、転送の開始時刻と終了時刻を最適化し、最適化された転送を返します。
