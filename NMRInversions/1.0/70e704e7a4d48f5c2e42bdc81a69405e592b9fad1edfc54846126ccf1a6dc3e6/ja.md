```
input2D(seq, x, y)
```

次のフィールドを含む構造体：

  * `seq` は2Dパルスシーケンス（例：IRCPMG）
  * `x_direct` は直接次元の取得パラメータ（例：CPMGエコーを取得する時刻）。
  * `x_indirect` は間接次元の取得パラメータ（例：IRシーケンスのすべての遅延時間τ）。
  * `data` は2Dデータ行列です。

これはinvert関数の入力として使用できます。
