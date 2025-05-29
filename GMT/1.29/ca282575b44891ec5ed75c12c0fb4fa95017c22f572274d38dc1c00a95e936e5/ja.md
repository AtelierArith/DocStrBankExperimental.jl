```
text(cmd0::String="", arg1=nothing; kwargs...)
```

可変サイズ、フォントタイプ、および方向のテキスト文字列をプロットします。さまざまな地図投影が提供されており、地図の境界を描画および注釈を付けるオプションがあります。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小BoundinBoxに設定されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **A** | **azimuth** | **azim** :: [Type => Bool]

    角度は方位として与えられます。現在の投影を使用して方向に変換します。
  * **C** | **clearance** :: [Type => Str]

    テキストと周囲のボックスとの間のクリアランスを設定します [15%]。
  * **D** | **offset** :: [Type => Str]

    投影された (x,y) 点からテキストを dx,dy だけオフセットします [0/0]。
  * **F** | **attrib** :: [Type => Str | Tuple]

    最大3つのテキスト属性（フォント、角度、整列）を指定します。
  * **G** | **fill** :: [Type => Str | Number]

    テキストボックスの塗りつぶしに使用される色またはシェードを設定します [デフォルトは塗りつぶしなし]。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **list** :: [Type => Bool]

    利用可能なフォント番号とフォント名をリストし、その後終了します。
  * **M** | **paragraph** :: [Type => Str | []]

    段落モード。
  * **N** | **no_clip** | **noclip** :: [Type => Str | []]

    地図の境界でテキストをクリップしません。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **change_case** :: [Type => Str]

    すべてのテキストを小文字または大文字に変更します。
  * **S** | **shade** :: [Type => Str | Tuple | Bool]		$Arg = [dx/dy][/shade]$

    テキストボックスの下にオフセットされた背景のシェード領域をプロットします（GMT6.2）。
  * **T** | **text_box** :: [Type => Str]

    Gおよび/またはWを使用する際のテキストボックスの形状を指定します。
  * **W** | **pen** :: [Type => Str]

    テキスト文字列の周りに矩形を描画するために使用されるペンを設定します。
  * **Z** | **threeD** :: [Type => Str]

    3-D投影の場合：各アイテムは3列目に与えられた独自のレベルを持つことを期待します。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図のフォーマットを選択します（例：figname="name.png"）

完全なドキュメントを見るには、次のように入力します: $@? pstext$ ```
