```
cornerplot(data; kwargs...)
```

nSamples-by-nDimensionsの配列を取り、次元のすべての組み合わせの密度プロットを作成します。入力変数間の相関を示すサブプロットの三角行列としてプロットします。入力`data`はMxN行列、`GMTdataset`、または`gmtread`で読み込むと`GMTdataset`を返すファイル名であることができます。

プロットは、対角線上に各列のヒストグラムがあり、サンプル数が<= 1000の場合は変数間の関係のための散布図または六角ビンプロットが含まれます。ただし、これは`kwargs`のオプションで変更できます。

  * `cornerplot(data)`: 多次元データセットのすべての2D投影をプロットします。
  * `cornerplot(..., varnames)`: 各次元の名前を印刷します。`varnames`はnDimensionsの長さの文字列のベクトルです。提供されない場合、`GMTdataset`の列名が使用されます。
  * `cornerplot(..., truths)`: プロット上に参照値を示します。
  * `cornerplot(..., quantile)`: 1-Dヒストグラムに垂直の破線として表示する分数分位数のリスト。
  * `cornerplot(..., hexbin=true)`: ポイント数が<= 1000のときでも六角ビンプロットを強制します。
  * `cornerplot(..., scatter=true)`: ポイント数が> 1000のときでも散布図を強制します。
  * `cornerplot(..., histcolor|histfill=color)`: 選択した色で対角ヒストグラムを塗りつぶします（histcolor=:noneで塗りつぶしなし）。

プロットの詳細を制御するために`kwargs`で使用できるいくつかのオプションがあり（`subplot`、`binstats`、および`plot`関数に渡されます）。

例:     cornerplot(randn(2500,3), cmap=:viridis, show=1)
