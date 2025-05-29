```
freecf(Z; mat="her", obj="kurt", opt="orth")
```

Zに自由成分分析を適用し、推定された混合行列と自由成分を返します。

# 引数

  * `Z`: matの行列の配列で、同じ次元を持つ
  * `mat`: Z[i]のタイプ、有効なオプションは"her"と"rec"
  * `obj`: 損失関数のタイプ、有効なオプションは"kurt"と"ent"
  * `opt`: 文字列、最適化のタイプ、有効なオプション: "orth", "sphe"

# 出力

  * `Aest`: サイズ`s`-by-`s`の行列、ここで`s` = size(Z, 1)
  * `Xest`: "自由"行列の配列、したがって`Z = Aest*Xest`
