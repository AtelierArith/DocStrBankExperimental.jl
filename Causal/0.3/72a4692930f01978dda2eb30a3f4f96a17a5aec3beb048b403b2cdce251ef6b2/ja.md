```julia
mutable struct Interpolant{TMB, INB, ITP}
```

`(tinit, coefinit)` と `(tfinal, coeffinal)` の間を補間する線形補間子を構築します。

# フィールド

  * `timebuf::Any`: 時間を記録するバッファ
  * `databuf::Any`: データを記録するバッファ
  * `itp::Any`: 内部補間関数
