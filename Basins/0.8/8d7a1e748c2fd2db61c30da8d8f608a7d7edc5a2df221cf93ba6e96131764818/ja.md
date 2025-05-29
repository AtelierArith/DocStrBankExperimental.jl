```
draw_basin!(xg, yg, integ, iter_f!::Function, reinit_f!::Function)
```

二次元平面上の引力盆地の推定値を計算します。これは低レベルの関数であり、高レベルの関数については、`basin_poincare_map`、`basin_discrete_map`、`basin_stroboscopic_map`を参照してください。

## 引数

  * `xg`, `yg` : テストする初期条件のグリッドを定義する1次元範囲ベクトル。
  * `integ` : 動的システムの積分器ハンドル。
  * `iter_f!` : マップまたはシステムを反復する関数。DifferentialEquations.jlのstep!を参照し、連続システムのポアンカレマップの例を参照してください。
  * `reinit_f!` : 位相空間の二次元投影でテストする初期条件を設定する関数。
