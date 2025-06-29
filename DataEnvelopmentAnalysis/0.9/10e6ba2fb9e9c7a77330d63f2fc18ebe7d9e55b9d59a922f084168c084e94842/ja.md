```
dea(X, Y)
```

入力 X と出力 Y に対してデータ包絡分析を使用して放射モデルを計算します。

# オプション引数

  * `orient=:Input`: 放射方向の入力モードを選択します。放射方向の出力モデルを選択するには `:Output` を選択します。
  * `rts=:CRS`: 定常規模の収益を選択します。変動規模の収益を選択するには `:VRS` を選択します。
  * `slack=true`: 入力と出力のスラックを計算します。
  * `Xref=X`: ユニットが評価される基準となる入力の参照セットを特定します。
  * `Yref=Y`: ユニットが評価される基準となる出力の参照セットを特定します。
  * `disposX=:Strong`: 入力の強い可処分性を選択します。弱い可処分性を選択するには `:Weak` を選択します。
  * `disposY=:Strong`: 出力の強い可処分性を選択します。弱い可処分性を選択するには `:Weak` を選択します。
  * `names`: 意思決定ユニットの名前を含む文字列のベクターです。
