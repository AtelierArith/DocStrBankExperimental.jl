```
coast(cmd0::String=""; kwargs...)
```

地図上に大陸、海岸線、河川、国境をプロットします。

地図上に灰色の陰影、色付き、またはテクスチャのある陸地 [または水域] をプロットし、[オプションで] 海岸線、河川、政治的境界を描画します。地図投影法を指定する必要があります。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図投影法を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **A** | **area** :: [Type => Str or Number]

    面積がmin*area km^2未満、または階層レベルがmin*level未満、またはmax_levelを超える特徴はプロットされません。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **river_fill** :: [Type => Str]

    湖や河川湖のための陰影、色、またはパターンを設定します。
  * **D** | **res** | **resolution** :: [Type => Str]		$Arg = c|l|i|h|f|a$

    使用するデータセットの解像度を選択します（(f)ull、(h)igh、(i)ntermediate、(l)ow、(c)rude）、または(a)uto）。
  * **E** | **DCW** :: [Type => Str]

    デジタル世界地図から国のポリゴンを描画またはダンプします。

      * Tuple("code", Str); Tuple(code, number); Tuple("code" [,"fill"], (pen)); Tuple((...),(...),...)
      * 例: ("PT",(0.5,"red","–")); (("PT","gblue",(0.5,"red"),("ES",(0.5,"yellow")))
      * ```
        DCW=:PT; DCW=(:PT, 1); DCW=("PT", :red)
        ```
  * **getR** | **getregion** | **get_region** :: [Type => Str]

    引数として渡されたコード/コードのリストに対応する地域を返します。
  * **F** | **box** :: [Type => Str]

    地図のスケールまたはバラの周りに長方形の境界を描きます。
  * **G** | **land** :: [Type => Str]

    「乾燥」地域の塗りつぶしまたはクリッピングを選択します。
  * **I** | **rivers** :: [Type => Str]

    河川を描きます。河川の種類を指定し、[オプションで] ペンの属性を追加します。
  * **L** | **map_scale** :: [Type => Str]

    地図スケールを描きます。
  * **M** | **dump** :: [Type => Str]

    単一のマルチセグメントASCII出力をダンプします。プロットは行われません。
  * **N** | **borders** :: [Type => Str]

    政治的境界を描きます。境界の種類を指定し、[オプションで] ペンの属性を追加します。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **clip** :: [Type => Str]		$Arg = land|water|end$

    陸地をクリップするには *clip=:land*、*clip=:water* は水をクリップします。既存のクリップパスの終わりを示すには *end* を使用します。投影情報は必要ありません。
  * **S** | **water** | **ocean** :: [Type => Str]

    「湿った」地域の塗りつぶしまたはクリッピングを選択します。
  * **Td** | **rose`** :: [Type => Str]

    参照点とアンカーポイントで定義された位置に地図の方向のバラを描きます。
  * **Tm** | **compass** :: [Type => Str]

    参照点とアンカーポイントで定義された位置に地図の磁気バラを描きます。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描きます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **W** | **shore** | **shorelines** | **coast** | **coastlines** :: [Type => Str]   海岸線を描きます [デフォルトは海岸線なし]。ペンの属性を追加します。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図の形式を選択します（例: figname="name.png"）

完全なドキュメントを見るには、次のように入力します: $@? coast$ ```
