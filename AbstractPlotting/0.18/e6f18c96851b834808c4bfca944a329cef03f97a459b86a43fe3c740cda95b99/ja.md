```
hist(values; bins = 15, normalization = :none)
```

`values`のヒストグラムをプロットします。`bins`は、`values`の範囲にわたってその数の等幅ビンを作成するための`Int`であることができます。あるいは、ビンのエッジのソートされた反復可能なオブジェクトであることもできます。ヒストグラムは`normalization`を設定することで正規化できます。可能な値は次のとおりです：

  * `:pdf`: 重みとビンサイズの合計で正規化します。結果として得られるヒストグラムはノルム1を持ち、PDFを表します。
  * `:density`: ビンサイズのみで正規化します。結果として得られるヒストグラムは入力のカウント密度を表し、ノルム1を持ちません。すでに密度を表している場合（`h.isdensity == 1`）、ヒストグラムは変更されません。
  * `:probability`: 重みの合計のみで正規化します。結果として得られるヒストグラムは各ビンの確率質量の割合を表し、ノルム1を持ちません。
  * `:none`: 正規化しません。

## 属性

`AbstractPlotting.Hist`の利用可能な属性とそのデフォルトは次のとおりです：

```
  bins           15
  cycle          [:color => :patchcolor]
  normalization  :none
```
