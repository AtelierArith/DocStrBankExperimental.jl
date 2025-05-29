```
write_step!( thdiag, time, degree, efield_dofs, bfield_dofs,
             efield_dofs_n, efield_poisson)
```

PICの診断情報を書き込む

  * `time` : 時間
  * `efield_dofs` : 電場
  * `efield_dofs_n` : 半ステップでの電場
  * `efield_poisson` : ポアソン方程式から計算された電場
  * `bfield_dofs` : 磁場
  * `degree` : スプラインの次数
