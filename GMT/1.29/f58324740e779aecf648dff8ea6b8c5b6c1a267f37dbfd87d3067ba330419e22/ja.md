```
grdfill(cmd0::String="", arg1=nothing, kwargs...)
```

ユーザーが何らかの方法で埋めたい未填充の穴を持つグリッドを読み込みます。穴はNaN値によって識別されますが、この基準は変更可能です。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdfill`](http://docs.generic-mapping-tools.org/latest/grdfill.html)を参照してください。

## パラメータ

  * **A** | **mode** :: [Type => Str]		$Arg = mode[arg]$

    使用する穴埋めアルゴリズムを指定します。定数埋めのためのcを選択し、定数値を追加するか、最近傍法のためのnを選択し、オプションでピクセル単位の検索半径を追加します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdfill(....)形式を使用してください。
  * **L** | **list** :: [Type => Str]	$Arg = [p]$

    各穴の西、東、南、北の長方形のサブリージョンをリストします。グリッドの埋め込みは行われず、**outgrid**は無視されます。オプションで、**p**を追加してすべてのサブリージョンの閉じたポリゴンを書き込むことができます。
  * **N** | **nodata** :: [Type => Str]	$Arg = nodata$

    穴のメンバーとしてポイントを識別するノード値を設定します [デフォルトはNaN]。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
