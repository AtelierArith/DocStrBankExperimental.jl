```
deaprofitgda(X, Y, W, P, measure)
```

データ包絡分析一般直接アプローチモデルを使用して、入力 `X`、出力 `Y`、入力の価格 `W`、出力の価格 `P`、および効率 `measure` に基づいて利益効率を計算します。

# 測定仕様:

  * `:ERG`: 拡張ラッセルグラフ（またはスラックベース測定（SBM））。

# オプション引数

  * `monetary=false`: 正規化された用語での分解。`true` の場合は貨幣的用語。
  * `atol=1e-6`: DMUが効率的と見なされるための許容誤差。
  * `names`: 意思決定単位の名前を含む文字列のベクター。
