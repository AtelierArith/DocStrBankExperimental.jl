```
struct SoftDTW{D, T} <: DTWDistance{D}
```

# 引数:

  * `γ`: スムージングパラメータ、デフォルトは1。小さい値は距離を標準DTWに近づけます。
  * `dist`: 内部距離、デフォルトは`SqEuclidean()`。
  * `transportcost`
