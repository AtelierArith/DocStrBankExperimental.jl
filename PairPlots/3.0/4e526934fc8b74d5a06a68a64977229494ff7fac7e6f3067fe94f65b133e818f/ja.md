```
pairplot(gridpos::Makie.GridLayout, inputs...; kwargs...)
```

主なPairPlots関数。Makieフィギュア内のグリッドレイアウトにプロットすることでペアプロットを作成します。

入力は、1つ以上の`Pair`のPairPlots.AbstractSeries => VizTypeのタプルである必要があります。

追加の引数：

  * labels: 列名（シンボル）から文字列、Makieリッチテキスト、またはLaTeX文字列へのDictを使用して軸ラベルをカスタマイズします。
  * diagaxis: 名前付きタプルのキーワード引数を使用して、対角線に沿ったプロットのMakie.Axisをカスタマイズします。
  * bodyaxis: 名前付きタプルのキーワード引数を使用して、対角線の下にあるプロットのMakie.Axisをカスタマイズします。
  * axis: 列名（シンボル）から軸設定の名前付きタプルへのDictを使用して、パラメータによって軸をカスタマイズします。`x`と`y`は、パラメータとサブプロットに基づいて自動的に前置されます。グローバルプロパティについては、`diagaxis`と`bodyaxis`を参照してください。
  * legend: 1つ以上の系列にラベルが付けられている場合に使用されるLegendコンストラクタへの追加のキーワード引数。もちろん、自分自身のLegendを作成し、フィギュアに挿入して完全に制御することもできます。
  * fullgrid: trueまたはfalse（デフォルト）。完全なグリッドを作成するために、対角線の上に重複したプロットを表示します。

## 例

基本的な使用法：

```julia
table = (;a=randn(1000), b=randn(1000), c=randn(1000))
pairplot(table)
```

ラベルをカスタマイズ：

```julia
pairplot(table, labels=Dict(:a=>L"\sum{a^2}"))
```

1つの変数に擬似対数スケールを使用：

```julia
pairplot(table, axis=(; a=(;scale=Makie.pseudolog10) ))
```
