```
deacostrussell(X, Y, W)
```

コスト効率を、入力 `X`、出力 `Y`、および入力の価格 `W` に対してラッセルデータ包絡分析を使用して計算します。

# オプション引数

  * `rts=:VRS`: 変動規模の収益を選択します。定常規模の収益を選択するには `:CRS` を選択します。
  * `monetary=false`: 正規化された用語での分解。`true` の場合は貨幣用語。
  * `names`: 意思決定単位の名前を含む文字列のベクター。
