```
deam(X, Y)
```

入力 X と出力 Y に対してデータ包絡分析を使用して放射状乗数モデルを計算します。

# オプション引数

  * `orient=:Input`: 放射状入力モードを選択します。放射状出力モデルを選択するには `:Output` を選択します。
  * `rts=:CRS`: 定常規模の収益を選択します。変動規模の収益を選択するには `:VRS` を選択します。
  * `Xref=X`: ユニットが評価される基準となる入力の参照セットを特定します。
  * `Yref=Y`: ユニットが評価される基準となる出力の参照セットを特定します。
  * `names`: 意思決定単位の名前を含む文字列のベクターです。
