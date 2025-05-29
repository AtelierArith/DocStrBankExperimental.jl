```
sphinterpolate(cmd0::String="", arg1=nothing, kwargs...)
```

球面上のデータの張力による球面グリッド化

完全なGMT（`GMT.jl`ではない）ドキュメントは[`sphinterpolate`](http://docs.generic-mapping-tools.org/latest/sphinterpolate.html)を参照してください。

## パラメータ

  * **D** | **skipdup** :: [Type => Bool]

    重複するポイントを削除します [デフォルトでは重複がないと仮定します]。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = sphinterpolate(....)の形式を使用してください。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで*y_inc*]はグリッド間隔です。オプションで、増分単位を追加します。
  * **Q** | **tension** :: [Type => Number | Str]     $Arg = mode[/options]$

    地元の形状特性を保持するか、弧の制約を満たすために張力係数を計算する4つの方法のいずれかを指定します。
  * **T** | **var_tension** :: [Type => Bool | Str]

    変数張力を使用します（-Q0 [定数]の場合は無視されます）。
  * **Z** | **scale** :: [Type => Bool | Str]

    補間の前に、データを最大データ範囲でスケーリングします [スケーリングなし]。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、値NaNに置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? sphinterpolate$
