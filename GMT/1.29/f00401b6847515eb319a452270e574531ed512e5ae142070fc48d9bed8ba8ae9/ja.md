```
grdproject(cmd0::String="", arg1=nothing, kwargs...)
```

地理的なグリッドデータセットを長方形のグリッドに投影するか、逆投影を行います。

完全なGMT（`GMT.jl`ではない）ドキュメントは、[`grdproject`](http://docs.generic-mapping-tools.org/latest/grdproject.html)を参照してください。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **C** | **center** :: [Type => Str | []]      $Arg = [dx/dy]$

    投影座標を投影中心に対して相対的にします [デフォルトは左下隅に対して相対的]。
  * **D** | **inc** :: [Type => Str | number]     $Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]$

    新しいグリッドの間隔を設定します。mを追加するとアーク分、sを追加するとアーク秒になります。
  * **E** | **dpi** :: [Type => Number]

    新しいグリッドの解像度をドット毎インチで設定します。
  * **F** | **one2one** :: [Type => Str]           $Arg = [c|i|p|e|f|k|M|n|u]$

    1:1スケーリングを強制します。つまり、出力（または入力、-Iを参照）データは実際の投影メートルである必要があります [e]。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdproject(....)の形式を使用してください。
  * **I** | **inverse** :: [Type => Bool]

    逆変換を行い、長方形から地理的に変換します。
  * **M** | **projected_unit** :: [Type => Str]    $Arg = c|i|p$

    cm、inch、またはpointが投影測定単位であることを示すためにc、i、またはpを追加します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのためにb、バイキュービック補間のためにc、バイリニア補間のためにl、または最近傍値のためにnを追加してグリッド補間モードを選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。

完全なドキュメントを見るには、次のように入力してください: $@? grdproject$
