```
grdvolume(cmd0::String="", arg1=nothing, kwargs...)
```

1つの2-Dグリッドを読み込み、xyzトリプレットを返します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdvolume`](http://docs.generic-mapping-tools.org/latest/grdvolume.html)を参照してください。

## パラメータ

  * **C** | **cont** | **contour** :: [Type => Str | List]   $Arg = cval or low/high/delta or rlow/high or rcval$

    cval等高線内の面積、体積、および平均高さ（体積/面積）を求めます。
  * **L** | **base_level** :: [Type => Number]          $Arg = base$

    等高線のレベルからベースまでの体積も追加します [デフォルトのベースは等高線です]。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **S** | **unit** :: [Type => Str]              $Arg = e|f|k|M|n|u$

    地理的グリッドの場合、e|f|k|M|n|uから単位を追加します [デフォルトはメートル（e）]。
  * **T** :: [Type => Str]                        $Arg = [c|h]$

    平均高さ（= 体積/面積）を最大化する単一の等高線を決定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **Z** | **scale** :: [Type => Str or List]     $Arg = fact[/shift]$

    オプションで、factによってデータをスケーリングする前にシフトを引きます。[デフォルトはスケーリングなし]。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    任意の順序で主な出力の特定のデータ列を選択します。

完全なドキュメントを見るには、次のように入力してください: $@? grdvolume$
