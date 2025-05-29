```
calc_changed_energy(mass; old_pc, dE) -> (pc, E_tot)
calc_changed_energy(species::Species; old_pc, dE) -> (pc, E_tot)
```

初期の `old_pc` 粒子の `momentum*c` とエネルギーの変化 `dE` が与えられたとき、最終的な `momentum*c` と総エネルギーを計算します。もし `dE` が大きすぎて負で解が存在しない場合は、`nothing, nothing` が返されます。すべての引数は `Numbers` ですが、`species` は `Species` 型です。

`mass` 引数は `energy/c^2` の単位です。

計算は精度を失わないように行われます。
