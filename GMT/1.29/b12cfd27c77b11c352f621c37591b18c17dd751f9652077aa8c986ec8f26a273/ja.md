```
grdimage(cmd0::String="", arg1=nothing, arg2=nothing, arg3=nothing; kwargs...)
```

各グリッドノードの中心に長方形をプロットし、z値に基づいてグレーの陰影（または色）を割り当てることによって、グレーの陰影（または色付き）の地図を生成します。

## パラメータ

  * **A** | **img_out** | **image_out** :: [Type => Str]

    PostScriptの代わりにラスタ形式で画像を保存します。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT名を指定するか、-Ccolor1,color2[,color3,...]を指定して、これらの色から自動的に線形連続CPTを構築します。
  * **D** | **img_in** | **image_in** :: [Type => Str]

    提供されたグリッドがGDALを介して読み込まれる画像ファイルであることを指定します。
  * **E** | **dpi** :: [Type => Int]

    作成される投影グリッドの解像度を設定します。
  * **G** | **bit_color** :: [Type => Int]
  * **I** | **shade** | **shading** | **intensity** :: [Type => Bool | Str | GMTgrid]

    (-1,+1)範囲の強度を持つグリッドファイルまたはGMTgridの名前、またはgrdgradientシェーディングフラグを指定します。
  * **M** | **monochrome** :: [Type => Bool]

    （テレビ）YIQ変換を使用してモノクロ画像への変換を強制します。
  * **N** | **noclip** :: [Type => Bool]

    地図の境界で画像をクリップしません。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **alpha_color** | **nan_alpha** :: [Type => Bool | Tuple | Str]	$Q = true | Q = (r,g,b)$

    z = NaNのグリッドノードを透明にするか、画像の透明度のための色を選択します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）。

完全なドキュメントを見るには、次のように入力してください: $@? grdimage$
