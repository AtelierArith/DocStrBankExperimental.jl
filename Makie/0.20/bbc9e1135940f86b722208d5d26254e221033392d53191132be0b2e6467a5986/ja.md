```
hist(values; bins = 15, normalization = :none)
```

`values`のヒストグラムをプロットします。`bins`は、`values`の範囲にわたってその数の等幅ビンを作成するための`Int`であることができます。あるいは、ビンのエッジのソートされた反復可能なオブジェクトであることもできます。ヒストグラムは`normalization`を設定することで正規化できます。可能な値は次のとおりです：

  * `:pdf`：重みとビンサイズの合計で正規化します。結果として得られるヒストグラムはノルム1を持ち、PDFを表します。
  * `:density`：ビンサイズのみで正規化します。結果として得られるヒストグラムは入力のカウント密度を表し、ノルム1を持ちません。すでに密度を表している場合（`h.isdensity == 1`）、ヒストグラムは変更されません。
  * `:probability`：重みの合計で正規化します。結果として得られるヒストグラムは各ビンの確率質量の割合を表し、ノルム1を持ちません。
  * `:none`：正規化しません。

統計的重みは`weights`キーワード引数を介して提供できます。

次の属性はヒストグラムを移動させることができ、複数のヒストグラムを1つのプロットに配置する際に便利です：

  * `offset = 0.0`：すべての値にオフセットを追加します
  * `fillto = 0.0`：バーの開始位置を定義します
  * `scale_to = nothing`：すべての値を特定の高さにスケーリングすることを許可します
  * `flip = false`：すべての値を反転させます

色は次のいずれかです：

  * `bins`の色のベクター
  * 単一の色
  * `:values`、ヒストグラムの値でバーに色を付けるため

## 属性

`MakieCore.Plot{Makie.hist}`の利用可能な属性とそのデフォルトは次のとおりです：

```
  bar_labels             "nothing"
  bins                   15
  color                  RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  cycle                  [:color => :patchcolor]
  fillto                 MakieCore.Automatic()
  flip_labels_at         Inf
  label_color            :black
  label_font             :regular
  label_formatter        Makie.bar_label_formatter
  label_offset           5
  label_size             20
  normalization          :none
  offset                 0.0
  over_background_color  MakieCore.Automatic()
  over_bar_color         MakieCore.Automatic()
  scale_to               "nothing"
  weights                MakieCore.Automatic()
```
