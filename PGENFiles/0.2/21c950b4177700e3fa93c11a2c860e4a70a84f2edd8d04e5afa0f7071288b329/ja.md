```
alt_allele_dosage!(buf, genobuf, p, v; genoldbuf)
```

ALTアレルの非相補的バイアレル量を計算します。

  * `buf`: 量の値を格納します。
  * `genobuf`: ジェノタイプの値を格納します。
  * `p`: `Pgen`オブジェクト。
  * `v`: `PgenVariant`オブジェクト。
  * `genoldbuf`: 最も最近の非LD圧縮されたジェノタイプ。

返すもの:

  * `buf`
  * `genobuf`
  * `offset`: 現在のバリアントレコードトラックの量レコードの終わり。
