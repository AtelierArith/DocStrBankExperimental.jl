# 2D反転のためのカーネル生成

```
create_kernel(seq, x_direct, x_indirect, X_direct, X_indirect, Data)
```

  * `seq` は2Dパルスシーケンス（例：IRCPMG）です。
  * `x_direct` は直接次元の取得パラメータ（例：CPMGエコーを取得する時刻）です。
  * `x_indirect` は間接次元の取得パラメータ（例：IRシーケンスのすべての遅延時間τ）です。
  * `X_direct` は直接次元における反転の出力「範囲」（例：IRCPMGにおけるT₂時間）です。
  * `X_indirect` は間接次元における反転の出力「範囲」（例：IRCPMGにおけるT₁時間）です。
  * `Data` は複素データの2Dデータ行列です。

出力は `svd_kernel_struct` です。
