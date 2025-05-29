```
tfer = match_transfer_patch_positions(tfer; atol=1., maxit=100)
```

パッチの時間と位置がパッチの両側で連続するように、転送の開始位置と終了位置を最適化しようとし、最適化された転送を返します。
