```
kml2gmt(cmd0::String="", arg1=nothing, kwargs...)
```

kml2gmt - Google Earth KMLファイルからGMTテーブルデータを抽出します

完全なGMT（`GMT.jl`ではない）ドキュメントは[`kml2gmt`](http://docs.generic-mapping-tools.org/latest/kml2gmt.html)を参照してください。

## パラメータ

  * **F** | **feature_type** :: [Type => Str]        $Arg = s|l|p$

    出力する特定のフィーチャタイプを指定します。ポイント（s）、ライン（l）、またはポリゴン（p）から選択します。デフォルトでは、すべてのジオメトリを出力します。
  * **Z** | **altitudes** :: [Type => Bool]

    高度座標をGMT z座標として出力します [デフォルトでは経度と緯度のみを出力します]。   (http://docs.generic-mapping-tools.org/latest/kml2gmt.html#z)
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **do** | **nodata_out** :: [Type => Str or Number]     $Arg = nodata$

    すべての出力列を調べ、任意の項目がNANに等しい場合は、選択した欠損データ値で置き換えます。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? kml2gmt$
