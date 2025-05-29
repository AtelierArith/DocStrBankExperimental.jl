```
colorbar(arg1=nothing; kwargs...)
```

地図上にグレースケールまたはカラースケールをプロットします。

  * **D** | **pos** | **position** :: [Type => Str]

    カラースケールの参照点を4つの座標系のいずれかを使用して地図上に定義します。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT名を指定するか、-Ccolor1,color2[,color3,...]を指定して、これらの色から自動的に線形連続CPTを構築します。
  * **F** | **box** :: [Type => Str]

    スケールの周りに矩形の境界を描画します。
  * **G** | **truncate** :: [Type => Str]  

    入力CPTを切り詰めて、最小および最大のzレベルをzloおよびzhiに設定します。
  * **I** | **shade** :: [Type => Number | Str]

    照明効果を追加します。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **equal** | **equal_size** :: [Type => Str | Bool]		`Arg = [i][gap]`

    同じサイズのカラーレクタングルを提供します。デフォルトでは、CPTのz範囲に応じて矩形のサイズをスケーリングします。
  * **M** | **monochrome** :: [Type => Bool]

    （テレビ）YIQ変換を使用してモノクロ画像に強制的に変換します。
  * **N** | **dpi** :: [Type => Str | Number]

    PostScript言語によってカラースケールがどのように表現されるかを制御します。
  * **Q** | **log** :: [Type => Str]

    対数補間スキームを選択します [デフォルトは線形]。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **S** | **appearance** | **nolines** :: [Type => Bool | []]

    異なるカラーレンジを黒いグリッド線で分けないようにします。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **W** | **scale** :: [Type => Number]

    提供されたスケールでCPT内のすべてのz値を乗算します。
  * **Z** | **zfile** :: [Type => Str]

    カラーエントリごとのカラーバー幅を含むファイルです。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図のフォーマットを選択します（例：figname="name.png"）

完全なドキュメントを見るには、次のように入力してください: $@? colorbar$
