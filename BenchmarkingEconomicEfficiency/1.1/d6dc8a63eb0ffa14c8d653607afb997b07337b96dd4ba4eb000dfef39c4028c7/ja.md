```
deacostrddf(X, Y, W, measure)
```

データ包絡分析の逆DDFモデルを使用して、入力 `X`、出力 `Y`、入力の価格 `W`、および効率 `measure` に基づいて利益効率を計算します。

# 測定仕様:

  * `:ERG`: 拡張ラッセルグラフスラックベースの測定。

# オプション引数

  * `rts=:VRS`: 定常規模の収益 `:CRS` または変動規模の収益 `:VRS` のいずれかを選択します。
  * `atol=1e-6`: DMUが効率的と見なされるための許容誤差。
  * `monetary=false`: 正規化された用語での分解。`true` の場合は貨幣用語。
  * `names`: 意思決定単位の名前を含む文字列のベクトル。
