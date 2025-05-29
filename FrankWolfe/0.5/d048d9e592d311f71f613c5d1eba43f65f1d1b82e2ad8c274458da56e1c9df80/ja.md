```
frank_wolfe(f, grad!, lmo, x0; ...)
```

フランク・ウォルフアルゴリズムの最も単純な形。タプル `(x, v, primal, dual_gap, traj_data)` を返します：

  * `x` 最終反復値
  * `v` LMOからの最後の頂点
  * `primal` プライマル値 `f(x)`
  * `dual_gap` 最終フランク・ウォルフギャップ
  * `traj_data` 軌道情報のベクトル。
