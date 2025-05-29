```
FDIModel <: AbstractFDDObject
```

故障検出および隔離問題を解決するために使用される合成モデルの型です。

`sysf::FDIModel` が合成モデルオブジェクトである場合、基礎となる記述子システムモデルは `sysf.sys` を介して取得でき、制御、外乱、故障、ノイズ、および補助ベクトルの次元はそれぞれ整数 `sysf.mu`、`sysf.md`、`sysf.mf`、`sysf.mw`、`sysf.ma` に含まれています。制御、外乱、故障、ノイズ、および補助入力のインデックスの範囲には、それぞれ `sysf.controls`、`sysf.disturbances`、`sysf.faults`、`sysf.noise`、`sysf.aux` を介してアクセスできます。
