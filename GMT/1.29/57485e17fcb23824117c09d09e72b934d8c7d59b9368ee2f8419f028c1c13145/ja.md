```
histogram(cmd0::String="", arg1=nothing; kwargs...)
```

最初のデータ列を調べて、提供されたビン幅に基づいてヒストグラムパラメータを計算します。あるいは、GMTimageおよびGMTgridオブジェクトのヒストグラムを直接表示します。オプション 'auto=true' または 'thresholds=(0, 0.1)' は、コントラスト強調（ヒストグラムストレッチ）に便利なヒストグラムの境界を見つけます。値は、境界を推定するために使用されるカウントの割合を表します。オプション 'zoom=true' は 'auto=true' を設定し、関心のある領域のみでヒストグラムを表示します。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **A** | **horizontal** :: [Type => Bool]

    ヒストグラムをx = 0から水平にプロットします [デフォルトはy = 0から垂直です]。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **color** | **cmap** :: [Type => Str | GMTcpt]

    CPTを指定します。各バーの中間x値を使用してバーの色を検索します。
  * **D** | **annot** | **annotate** | **counts** :: [Type => Str | Tuple]

    各バーにそのバーが表すカウントを注釈します。
  * **E** | **width** :: [Type => Bool]			`Arg = width[+ooffset]`

    Tを介して設定されたデフォルトとは異なるヒストグラムバーの幅を使用し、オプションで全てのバーをオフセットでシフトします。
  * **binmethod** | *BinMethod** :: [Type => Str]			`Arg = method`

    ビンニングアルゴリズム："scott"、"fd"、"sturges"または浮動小数点データ用の"sqrt"。DateTimeデータ用の"second"、"minute"、"hour"、"day"、"week"、"month"または"year"。
  * **F** | **center** :: [Type => Bool]

    各値の中央ビンを設定します。[デフォルトは左端です]。
  * **G** | **fill** :: [Type => Number | Str]

    バーの塗りつぶしを選択します [G、LまたはCが設定されていない場合はG=100]。
  * **I** | **inquire** | **bins** :: [Type => Bool | :O | :o | bins=(all=true,) | bins=(no_zero=true,) ]

    ビンニング後の最小/最大xおよびyについて問い合わせるか、ビン化された配列を出力します。
  * **L** | **out_range** :: [Type => Str]			`Arg = l|h|b`

    **T**によって設定された範囲の外にある極端な値の処理。
  * **N** | **distribution** | **normal** :: [Type => Str]

    同等の正規分布を描画します; 希望するペンを追加します [0.5p,black]。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **cumulative** :: [Type => Bool | "r"]

    累積ヒストグラムを描画します。rを追加すると、逆累積ヒストグラムを計算します。
  * **R** | **region** :: [Type => Str]

    (r,azimuth)空間での関心のある「領域」を指定します。r0は0、r1は単位の最大長です。
  * **S** | **stairs** :: [Type => Str | number]

    デフォルトのヒストグラムの内部バーを含まない階段状の図を描画します。
  * **T** | **range** | **bin** :: [Type => Str]			`Arg = [min/max/]inc[+n] | file|list]`

    minからmaxまでのビン境界の均等に間隔を空けた配列を作成します。min/maxが指定されていない場合、`region`の範囲がデフォルトになります。定数ビン幅を使用するには`bin=val`を使用します。
  * **W** | **pen** :: [Type => Str | Tuple]

    セクターのアウトラインまたはバラプロットのペン属性を設定します。[デフォルトはアウトラインなし]。
  * **Z** | **kind** :: [Type => Number | Str]

    6種類のヒストグラムの中から選択します。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）

完全なドキュメントを見るには、次のように入力します: $@? histogram$ ```
