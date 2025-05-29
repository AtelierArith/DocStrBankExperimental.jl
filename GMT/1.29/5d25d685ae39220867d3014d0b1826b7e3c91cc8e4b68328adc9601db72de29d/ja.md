```
mbimport(cmd0::String="", arg1=nothing, arg2=nothing, arg3=nothing; kwargs...)
```

各グリッドノードの中心に長方形をプロットし、z値に基づいてグレーのシェード（または色）を割り当てることによって、グレーのシェード（または色付き）のマップを生成します。

## パラメータ

  * **A** | **footprint** :: [Type => Str | Tuple]	$Arg = factor/mode/depth$

    ビームまたはピクセルのフットプリントの沿軌道次元がどのように計算されるかを決定します。
  * **J** | **proj** | **projection** :: [Type => String]

    マップ投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT名を指定するか、-Ccolor1,color2[,color3,...]を指定して、これらの色から自動的に線形連続CPTを構築します。
  * **D** | **scaling** :: [Type => Str | Tuple]	$Arg = mode/scale/min/max$

    プロット前に適用できるビーム振幅またはサイドスキャンピクセル値のスケーリングを設定します。
  * **E** | **dpi** :: [Type => Int]

    作成される投影画像の解像度を設定します。
  * **G** | **bit_color** :: [Type => Str | Tuple]	$Arg = magnitude/azimuth or magnitude/median$

    浅海のシミュレーションされた照明を制御するパラメータを設定します。
  * **S** | **speed** :: [Type => Number]

    入力データで許可される最小速度をkm/hr（5.5ノット〜10 km/hr）で設定します。
  * **T** | **timegap** :: [Type => number]

    隣接するピング間の最大時間ギャップを分単位で設定します。
  * **Z** | **type_plot** :: [Type => Str | Number]

    プロットのスタイルを設定します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さの単位(c, i, または p)を追加します。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのためにbを追加することでグリッド補間モードを選択します。bicubic補間のためにc、バイリニア補間のためにl、または最近傍値のためにnを追加します。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]です。
