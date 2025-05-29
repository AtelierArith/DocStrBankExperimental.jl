```
grdinfo(cmd0::String="", arg1=nothing; kwargs...)
```

2次元グリッドファイルを読み込み、グリッドファイル内の(x,y,z)データに関するメタデータとさまざまな統計情報を報告します。

## パラメータ

  * **C** | **oneliner** | **numeric** :: [Type => Str | Number]

    タブ区切りのフィールドを使用して、単一行でレポートをフォーマットします。
  * **D** | **tiles** :: [Type => Number | Str]  

    単一のグリッドのドメイン（またはグリッドが指定されていない場合は-Rドメイン）を、dxとdyのサイズのタイルに分割します（-Iで設定）。
  * **E** | **extrema** | **extreme** :: [Type => Bool]

    列ごと（E=:x）または行ごと（E=:y）に見つかった極値を報告します。
  * **F** | **report_ingeog** :: [Type => Bool]

    世界地図形式でグリッドドメインとx/yインクリメントを報告します。
  * **G** | **download** :: [Type => Bool]

    要求された情報を報告するために、タイル状のグローバルリモートグリッドのすべてのタイルのダウンロードとモザイキングを強制します（可能な場合）。
  * **I** | **nearest** :: [Type => Number | Str]     $Arg = [dx[/dy]|b|i|r]$

    dxとdyの最も近い倍数に対する領域の最小/最大を報告し、これを-Rw/e/s/nの形式で出力します。
  * **L** | **force_scan** :: [Type => Number | Str]

    実際にデータをスキャンした後に統計を報告します。
  * **M** | **minmax_pos** :: [Type => Bool]

    最小/最大のz値の位置を見つけて報告します。
  * **Q** | **cube** :: [Type => Bool]

    入力ファイルは3次元のnetCDFデータキューブでなければなりません。**D**、**E**、**F**、および**Ib**（GMT6.2）とは互換性がありません。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **T** | **minmax** :: [Type => Number | Str]   最小および最大のz値を決定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    任意の順序で、主要な出力のための特定のデータ列を選択します。

完全なドキュメントを見るには、次のように入力してください: $@? grdinfo$
