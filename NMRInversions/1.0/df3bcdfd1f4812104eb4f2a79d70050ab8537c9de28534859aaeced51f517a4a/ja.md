# 1Dデータの反転のためのカーネルを作成する。

```
create_kernel(seq, x, X)
```

  * `seq` はパルスシーケンス（例：IR、CPMG、PFG）
  * `x` は実験のx軸（時間またはb因子など）
  * `X` は出力x軸の範囲（T1、T2、Dなど）

出力は行列 `K` です。
