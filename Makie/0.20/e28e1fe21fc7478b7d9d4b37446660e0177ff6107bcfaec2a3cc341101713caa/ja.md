```
stephist(values; bins = 15, normalization = :none)
```

`values`のステップヒストグラムをプロットします。`bins`は、`values`の範囲にわたってその数の等幅ビンを作成するための`Int`であることができます。あるいは、ビンのエッジのソートされた反復可能なオブジェクトであることもできます。ヒストグラムは、`normalization`を設定することで正規化できます。

ほとんどのオプションは`hist`プロット関数と共有されています。

統計的な重みは、`weights`キーワード引数を介して提供できます。

以下の属性はヒストグラムを移動させることができ、複数のヒストグラムを1つのプロットに配置する際に便利です：

  * `scale_to = nothing`: すべての値を特定の高さにスケーリングすることを許可します

## 属性

`MakieCore.Plot{Makie.stephist}`の利用可能な属性とそのデフォルトは次のとおりです：

```
  bins           15
  color          RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  cycle          [:color => :patchcolor]
  linestyle      :solid
  normalization  :none
  scale_to       "nothing"
  weights        MakieCore.Automatic()
```
