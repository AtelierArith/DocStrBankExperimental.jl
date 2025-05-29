```
grdhisteq(cmd0::String="", arg1=nothing, kwargs...)
```

与えられたグリッドファイルを等しい面積のパッチに分割するデータ値を見つけます。grdhisteqの一般的な使用法の1つは、画像のヒストグラム均等化の一種です。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdhisteq`](http://docs.generic-mapping-tools.org/latest/grdhisteq.html)を参照してください。

## パラメータ

  * **C** | **ncels** | **n_cels** :: [Type => Number]

    データ範囲をいくつのセル（または分割）にするかを設定します [16]。
  * **D** | **dump** :: [Type => Str or []]

    ファイルにレベル情報をダンプするか、ファイルが提供されていない場合は標準出力に出力します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdhisteq(....)の形式を使用してください。
  * **N** | **gaussian** :: [Type => Number or []]

    ガウス出力。
  * **Q** | **quadratic** :: [Type => Bool]

    二次出力。二次ヒストグラム均等化を選択します。[デフォルトは線形です]。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。

完全なドキュメントを見るには、次のように入力してください: $@? grdhisteq$
