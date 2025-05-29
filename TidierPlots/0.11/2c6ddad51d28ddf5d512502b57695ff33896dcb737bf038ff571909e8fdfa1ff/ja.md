```
geom_point(aes(...), ...)
geom_point(plot::GGPlot, aes(...), ...)
```

ポイントジオムは散布図を作成するために使用されます。散布図は、2つの連続変数間の関係を表示するのに最も便利です。1つの連続変数と1つのカテゴリ変数、または2つのカテゴリ変数を比較するためにも使用できますが、他のチャートの方が通常は適切です。バブルチャートは、3つ目の変数がポイントのサイズにマッピングされた散布図です。

# 引数

  * `plot::GGPlot` (オプション): このジオムを追加するプロットオブジェクト。これは通常、@chainの一部としてggplotを作成するのを容易にするために使用されます。
  * `data` (DataFrame): このジオムに使用するデータ。提供されない場合、ジオムはggplotからデータを継承します。
  * `aes(...)`: マッピングに使用されるDataFrameの列の名前
  * `inherit_aes`: ジオムはggplotからaesを継承すべきか？
  * `...`: 列にマッピングされていないオプション（Makie.Scatterに渡される）

# オーバープロット

散布図の最大の潜在的な問題はオーバープロットです：ポイントが数個以上ある場合、ポイントが互いに重なってプロットされる可能性があります。これはプロットの視覚的外観を著しく歪める可能性があります。この問題に対する唯一の解決策はありませんが、役立ついくつかの技術があります。geom*smooth()を使用して追加情報を加えることができますし、ユニークなx値が少ない場合は、geom*boxplot()も有用です。別の技術は、ポイントを透明にすること（例：geom*point(alpha = 0.05)）や非常に小さくすること（例：geom*point(shape = '.')）です。

# 必須の美学

  * `x`
  * `y`

# オプションの美学 (see [`aes`](@ref))

  * `color` / `colour`
  * `fill`
  * `shape`
  * `size`
  * `stroke`

# オプションの引数

  * `color` / `colour`
  * `colormap` / `palette`
  * `marker` / `shape`
  * `markersize` / `size`
  * `strokewidth` / `stroke`
  * `strokecolor` / `strokecolour`
  * `glowwidth` / `glow`
  * `glowcolor` / `glowcolour`
  * `alpha`

# 例

```julia
p = ggplot(penguins, @aes(bill_length_mm, bill_depth_mm))
p + geom_point()

# 美学マッピングを追加
p + geom_point(aes(colour = :sex))
```
