```
grd2kml(cmd0::String="", arg1=nothing, kwargs...)
```

2-D グリッドファイルを読み込み、選択したタイルサイズ [256x256 ピクセル] を使用して、PNG 画像と Google Earth 用の KML ラッパーのクワッドツリーを作成します。

## パラメータ

  * **A** | **mode** :: [Type => Str]		`Arg = url`

    Google Earth によって認識される 3 つの高度モードのいずれかを選択し、タイルレイヤーの高度 (m) を決定します。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT 名を指定するか、-Ccolor1,color2[,color3,...] を指定して、これらの色から自動的に線形連続 CPT を構築します。
  * **E** | **url** :: [Type => Str]		`Arg = url`

    ファイルをローカルでホストする代わりに、サイトの URL を前置きします。トップレベルの prefix.kml ファイルは、この URL を使用して参照する他のファイルを見つけます。
  * **F** | **filter** :: [Type => Str]

    より遠くからの表示のためにグリッドのダウンサンプリングに使用するフィルターを指定します。ボックスカー、コサインアーチ、ガウス、またはメディアン [ガウス] の中から選択します。
  * **H** | **sub_pixel** | **subpixel** :: [Type => Int]         `Arg = factor`

    psconvert にサブピクセルスムージングファクターを渡すことで、ラスタライズの品質を向上させます。
  * **I** | **shade** | **shading** | **intensity** :: [Type => Str | GMTgrid]

    (-1,+1) 範囲の強度を持つグリッドファイルまたは GMTgrid の名前、または grdgradient シェーディングフラグを指定します。
  * **L** | **tilesize** | **tile_size** :: [Type => Number]			`Arg = tilesize`

    画像のビルディングブロックの固定サイズを設定します。2 の冪である整数でなければなりません。典型的な値は 256 または 512 [256] です。
  * **N** | **prefix** [Type => Str]		            `Arg = prefix`

    トップレベルの KML ファイル名と、すべての参照 KML ファイルおよび PNG 画像が書き込まれるディレクトリに使用される一意の名前プレフィックスを設定します [GMT_Quadtree]。
  * **Q** | **nan_t** | **nan_alpha** :: [Type => Bool]

    z = NaN のグリッドノードを透明にし、PostScript Level 3 のカラーマスキング機能を使用します。
  * **S** | **extra_layers** | **extralayers** :: [Type => Str]

    データのフル解像度をキャプチャするために必要なものを超える追加のレイヤーを追加します。
  * **T** | **title** :: [Type => Str]		        `Arg = title`

    トップレベルのドキュメントのタイトル (すなわち、その説明) を設定します。
  * **W** | **contours** :: [Type => Str]		        `Arg = title`

    各レコードが等高線値と等高線ペンを保持するファイルを提供します。

完全なドキュメントを見るには、次のように入力します: $@? grd2kml$ ```
