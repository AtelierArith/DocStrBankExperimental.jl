```
iterative_DEJMPS_protocol(ρ, targetFid, n, d, stdBasis, maxIts)
```

`d=2` 次元の `n` コピー入力状態 `ρ` に DEJMPS ルーチンの反復を適用します。 `targetFid` または最大反復回数 `maxIts` に達するまで反復します。 `targetFid` に到達できた場合は `distillable=true` を返し、各反復に対する `stdbasis` に関する忠実度と成功確率を返します。
