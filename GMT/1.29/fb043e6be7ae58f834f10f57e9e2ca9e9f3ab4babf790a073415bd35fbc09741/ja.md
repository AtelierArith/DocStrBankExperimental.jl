```
trend2d(cmd0::String="", arg1=nothing, kwargs...)
```

z = f(x,y) のために [weighted] [robust] 多項式モデルを xyz[w] データにフィットさせます。

完全な GMT (GMT.jl ではない) ドキュメントは [`trend2d`](http://docs.generic-mapping-tools.org/latest/trend2d.html) を参照してください。

## パラメータ

  * **F** | **out** | **output** :: [Type => Str]   $Arg = xyzmrw|p$

    出力の列を作成するために、{x y m r w} のセットから最大5文字を任意の順序で指定します。
  * **N** | **model** :: [Type => Str]      $Arg = n_model[+r]$

    モデルの項数 n_model を指定し、+r を追加してロバストフィットを行います。例: ロバストバイリニアモデルは N="4+r" です。
  * **C** | **condition_number** :: [Type => Number]   $Arg = condition_number$

    行列解のための最大許容条件数を設定します。
  * **I** | **conf_level** :: [Type => Number | []]   $Arg = [confidence_level]$

    モデルパラメータの数を反復的に増やし、1から始めて n*model に達するか、モデルの分散の減少が信頼*レベルで有意でない場合まで続けます。
  * **W** | **weights** :: [Type => Str | []]     $Arg = [+s]$

    重みは入力列4に供給されます。重み付き最小二乗フィットを行うか、反復ロバストフィットを行う際にこれらの重みから始めます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告を stderr に送信する冗長性レベルを選択します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値が GMT の公式 NaN 値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します (時間または地理データ)。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主な入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主な入力の特定のデータ列を任意の順序で選択します。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを周期的座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? trend2d$
