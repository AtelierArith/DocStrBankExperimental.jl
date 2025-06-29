```
boxplot(data, grp=[]; pos=nothing, kwargs...)
```

  * `data`: ベクトル（単一のボックスをプロット）、行列（n列のボックスをプロット）、MxNxG（`G`グループの`N`列ボックスをプロット）、ベクトルのベクトル（異なるサイズのデータからn列ボックスをプロット）、ベクトルのベクトルのベクトル（Gグループ - length(data) -、グループは要素数が可変であり、それぞれ独自のサイズを持つ）。
  * `grp`: データ列ベクトルをカテゴリ（グループ）に分解するために使用されるカテゴリカルベクトル（整数またはテキスト文字列で構成）。
  * `pos`: ボックスをプロットする座標ベクトル（または`data`がベクトルの場合は単一の位置）。デフォルトでは1:n*boxesまたは1:n*groupsにプロットされる。
  * `ccolor`: グループが定数の色を持つか（`fill=true`が使用される場合）、可変の色を持つか（デフォルト）を示す論理値。
  * `fill`: `fill=true`の場合、ボックスを事前定義されたカラースキームで塗りつぶす。そうでない場合は、ボックスを塗りつぶすための色のリストを提供。
  * `fillalpha` : `fill`オプションが使用されるとき、[0-1]または]1-100]の間の数値を持つ配列（ベクターまたは1行行列）を受け取るこのオプションで塗りつぶされたボックスの透明度を設定できる。

```
      ここで100（または1）は完全な透明度を意味します。
```

  * `boxwidth`または`cap`: ボックスプロットの幅と、オプションでキャップの幅を設定します。`boxwidth="10p/3p"`のように情報を提供して、ボックス幅をキャップの幅とは異なるように設定します。ただし、これはGMT6.5が必要です。以前のバージョンではボックスとキャップの幅を区別しません。
  * `groupWidth`: 各xグループのボックスが広がるべきx軸の間隔の割合を指定します。デフォルトは0.75です。
  * `notch`: ボックスにノッチがあるべきかどうかを示す論理値。
  * `outliers`: NamedTuple以外の場合、デフォルトの黒い5pt星で外れ値（1.5IQR）をプロットします。引数がNamedTuple（marker=??、size=??、color=??、markeredge=??）の場合、`marker`が`plots`のマーカーシンボルの1つであるとき、外れ値をその仕様でプロットします。欠落している仕様は上記の値にデフォルトします。すなわち、`outliers=(size="3p")`は黒い3pt星をプロットします。
  * `horizontal`または`hbar`: 垂直ボックスプロットの代わりに水平にプロットします。
  * `weights`: `data`のデータに対する重みを与える配列。配列は`data`と同じサイズでなければなりません。
  * `region`または`limits`: デフォルトではプロットの制限を推定しますが、時にはそれが便利でない場合があります。プロットの制限を制御したい場合は、region=(x*min,x*max,y*min,y*max)のタプルを提供します。
  * `separator`: = trueの場合、グループを分ける黒い線をプロットします。そうでない場合は、それらの線のペン設定を提供します。
  * `ticks`または`xticks`または`yticks`: 注釈の間隔とラベルを持つタプル。例えば、xticks=(1:5, ["a", "b", "c", "d"])のように、最初の要素はAbstractArrayで、2番目は文字列またはシンボルの配列またはタプルです。
