```
psi = applyOps!(psi,sites,Op[,trail=ones(1,1)])
```

演算子 `Op` (任意の `TensType`) を、整数のベクトルであるサイト `sites` に対して MPS `psi` にインプレースで適用します。デフォルトでない場合、トレーリング演算子 `trail` を適用することができます。
