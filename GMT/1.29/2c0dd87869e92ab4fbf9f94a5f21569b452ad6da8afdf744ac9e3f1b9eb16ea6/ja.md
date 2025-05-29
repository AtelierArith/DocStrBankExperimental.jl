```
grdview(cmd0::String="", arg1=nothing, arg2=nothing, arg3=nothing; kwargs...)
```

2-D グリッドを読み込み、メッシュを描画したり、多角形で構成された色付き/グレースケールの表面を塗装したり、これらの多角形をラスタ画像にスキャンライン変換することによって 3-D パースペクティブプロットを生成します。

  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは 15x10 cm の線形（非投影）地図です。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT 名を指定するか、-Ccolor1,color2[,color3,...] を指定して、これらの色から自動的に線形連続 CPT を構築します。
  * **G** | **drape** | **drapefile** :: [Type => Str | GMTgrid | a Tuple with 3 GMTgrid types]

    relief_file によって提供された地形の上に drapefile の画像をドレープします。
  * **I** | **shade** | **shading** | **intensity** :: [Type => Str | GMTgrid]		$Arg = GMTgrid | filename$

    (-1,+1) 範囲の強度を持つグリッドファイルまたは GMTgrid の名前、または grdgradient シェーディングフラグを指定します。
  * **N** | **plane** :: [Type => Str | Int]		$Arg = (level [,fill])$

    この z レベルで平面を描画します。
  * **P** | **portrait** :: [Type => Bool or []]

    GMT にポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **surftype** | **surf** :: [Type => Str | Int] $Arg = mesh=Bool, surface=Bool, image=Bool, wterfall=(:rows|cols,[fill])$

    **m** をメッシュプロット、**s** を表面、**i** を画像として指定します。
  * **S** | **smoothfactor** :: [Type => Number]

    おおよそ (gridbox_size/smoothfactor) 間隔で等高線を再サンプリングするために使用されます。
  * **T** | **tiles** | **no_interp** :: [Type => Str | NT]	$Arg = (skip|skip_nan=Bool, outlines=Bool|pen)$

    補間なしで画像をプロットします。
  * **W** | **pens** | **pen** :: [Type => Str]	$Arg = (contour=Bool|pen, mesh=Bool|pen, facade=Bool|pen)$

    等高線、メッシュ、またはファサードを描画します。ペン属性を追加します。
  * **isgeog** :: [Type => Any]

    投影情報を持つ画像を地理的なグリッドの上にドレープする際に、この事実に関する情報を持たない場合、プログラムが共通のバウンディングボックスを見つけるのを助けるためにこのオプションを使用する必要があります。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図のフォーマットを選択します（例: figname="name.png"）

完全なドキュメントを見るには、次のコマンドを入力してください: $@? grdview$
