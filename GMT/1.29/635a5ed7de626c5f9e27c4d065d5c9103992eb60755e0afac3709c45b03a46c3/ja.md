```
ternary(cmd0="", arg1=nothing; image=false, clockwise=false, kwargs...)
```

テーブル [またはファイル] から (a,b,c[,z]) レコードを読み取り、三元図上のその位置に画像とシンボルをプロットします。

  * **B** | **frame** :: [Type => NamedTuple | Str] –

    三元図では、三つの辺は a (底)、b (右)、c (左) と呼ばれます。デフォルトでは、軸にラベルを付けずに注釈を付け、グリッド線を描画します。しかし、ラベル付けは非常に重要な機能であるため、3つの軸のラベルを含む3要素のタプルを引数として受け取る `labels` オプションを使用できます。注釈やグリッドの間隔（オン/オフ）に関するさらなる制御は、`frame=(annot=?, grid=?, alabel=?, blabel=?, clabel=?, suffix=?)` 形式を使用することで達成されます。このモジュールでは一般的な `frame` オプションのすべてのオプションが受け入れられるわけではなく、より詳細なフレームオプションの選択には、`frame="<arg> <arg> <arg>"` の形式で純粋な GMT 構文に頼る必要があります。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT 名を指定するか、-Ccolor1,color2[,color3,...] を指定して、これらの色から自動的に線形連続 CPT を構築します。
  * **G** | **fill** :: [Type => Str] –

    バーの塗りつぶしに使用する色またはパターンを選択します。
  * **L** | **vertex_labels** :: [Type => Str | Tuple of strings] –		`Arg = a/b/c`

    コンポーネントが 100% の三元図の3つの頂点のラベルを設定します [なし]。
  * **M** | **dump** :: [Type => Str]

    変換された入力 (a,b,c[,z]) レコードを直交座標 (x,y,[,z]) レコードにダンプします。ここで、x, y は三角形上の正規化された座標です（すなわち、x は 0–1、y は 0–sqrt(3)/2）。プロットは行われません。
  * **N** | **no_clip** | **noclip** :: [Type => Str or []]

    地図の境界の外にあるシンボルをクリップしないでください。
  * **R** | **region** | **limits** :: [Type => Tuple | Str]

    各軸 a, b, c の最小および最大限界を指定します。デフォルトは (0,100,0,100,0,100) です。
  * **S** | **symbol** :: [Type => Str]

    三元図に個々のシンボルをプロットします。`S` が指定されていない場合は、代わりに線（`pen` が必要）または多角形（`color` または `fill` が必要）をプロットします。

    また、エイリアスを使用してシンボルのサブセットを選択できます: **symbol** または **marker** と値:

      * **-**, **x_dash**
      * **+**, **plus**
      * **a**, *, **star**
      * **c**, **circle**
      * **d**, **diamond**
      * **g**, **octagon**
      * **h**, **hexagon**
      * **i**, **v**, **inverted_tri**
      * **n**, **pentagon**
      * **p**, **.**, **point**
      * **r**, **rectangle**
      * **s**, **square**
      * **t**, **^**, **triangle**
      * **x**, **cross**
      * **y**, **y_dash**

    そして、**markersize** または **size** キーワードでサイズを選択します [デフォルトは 8p]。マーカーサイズはスカラーまたはデータの行数と同じサイズのベクトルであることができます。単位は指定されていない限りポイントです（例えば cm の場合は *par=(PROJ*LENGTH*UNIT=:c,)*）。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットに GMT タイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートを stderr に送信する冗長性レベルを選択します。
  * **W** | **pen** :: [Type => Str | Number]

    特定の線の属性を設定します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して (x-shift,y-shift) だけシフトし、オプションで長さの単位 (c, i, または p) を追加します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常に ASCII です）。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目が nodata に等しい場合、この値を欠損データ項目として解釈し、値 NaN に置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続するデータポイント間の間隔を調べ、線にブレークを課します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点を選択し、視点の方位角と高度を設定します [180/90]。
  * **q** | **inrow** | **inrows** :: [Type => Str]       $Arg = [i|o][~]rows[+ccol][+a|f|s]$

    読み取る特定のデータ行を選択します (-qi [デフォルト]) または書き込みます (-qo) [すべて]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイの PDF 透明度レベルを設定します（0-100] パーセント範囲で。 [デフォルトは 0、すなわち不透明]。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図の形式を選択します（例: figname="name.png"）

上記のオプション以外に、`kwargs` 入力は以下のオプションも受け入れます。

  * `image`: - `surface` で補間されたグリッドから `grdimage` を使用して自動的に計算された画像で三元プロットを塗りつぶします。
  * `contour`: - このオプションは2つの異なる方法で機能します。`image` と一緒に使用すると、`grdcontour` を呼び出して等高線をオーバーレイします。しかし、単独で使用すると、`contour` を呼び出して等高線を作成します。違いは重要で、このオプションは `contour=true` の *デフォルトモード* で使用でき、数と注釈付き等高線が自動的に選択されます。または、ユーザーはそのモジュールに適したすべてのオプションを含む NamedTuple を引数として渡すことで完全な制御を行うことができます。*例:* `contour=(cont=10, annot=20, pen=0.5)`
  * `contourf`: - *スタンドアロン* `contour` のように機能します。`contourf=true` を使用すると、自動パラメータを使用して塗りつぶされた等高線を作成します。`contourf=(...)` 形式で等高線モジュールのオプションを選択できます。
  * `clockwise`: - 正の軸の方向が時計回りであることを示すために `true` に設定します [デフォルトでは a, b, c 軸が反時計回りの方向で正となります]。
