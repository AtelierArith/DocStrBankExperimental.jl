```
sphtriangulate(cmd0::String="", arg1=nothing, kwargs...)
```

球面の経度、緯度データのデローニーまたはボロノイ構築

完全なGMT（`GMT.jl`ではない）ドキュメントは[`sphtriangulate`](http://docs.generic-mapping-tools.org/latest/sphtriangulate.html)を参照してください。

## パラメータ

  * **A** | **area** :: [Type => Bool]

    球面三角形（Qd）または多角形（Qv）の面積を計算し、出力セグメントヘッダーに面積を書き込みます。
  * **C** | **save_mem** :: [Type => Bool]

    大規模データセットの場合、メモリを節約できます（処理が増える代償として）。
  * **D** | **skipdup** :: [Type => Bool]

    重複するポイントを削除します [デフォルトでは重複がないと仮定します]。
  * **L** | **unit** :: [Type => Str]          $Arg = e|f|k|m|n|u|d$

    距離と面積の計算に使用する単位を指定します。
  * **N** | **nodes** :: [Type => Str]         $Arg = `file$

    各多角形に関する情報を別のファイルに書き込みます。
  * **Q** | **voronoi** :: [Type => Str]     $Arg = d|v$

    Delaunay三角形にはdを、Voronoi多角形にはvを追加します [デローニー]。
  * **T** | **arcs** :: [Type => Bool | Str]

    構築のユニークな弧を書き込みます [デフォルトでは埋められる三角形または多角形を書き込みます]。 -Aと一緒に使用すると、選択した単位でセグメントヘッダーに弧の長さを保存します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主な入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主な入力の特定のデータ列を任意の順序で選択します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? sphtriangulate$
