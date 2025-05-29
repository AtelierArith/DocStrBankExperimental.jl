```
mc_volumes(xs::Points, nmc=1000)
```

`xs`によって生成されたボロノイセルの面積と体積を`nmc`モンテカルロサンプルを使用して推定します。

# 戻り値

  * `SparseMatrix`: 2つのセルの共通境界の面積
  * `Vector`: 各セルの体積
