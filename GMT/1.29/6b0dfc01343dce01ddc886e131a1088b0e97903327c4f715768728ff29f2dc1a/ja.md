```
trend1d(cmd0::String="", arg1=nothing, kwargs...)
```

y = f(x) に対して xy[w] データのための [加重] [ロバスト] 多項式/フーリエモデルをフィットします。

完全な GMT ( `GMT.jl` ではなく) ドキュメントは [`trend1d`](http://docs.generic-mapping-tools.org/latest/trend1d.html) を参照してください。

## パラメータ

  * **F** | **out** | **output** :: [Type => Str]   $Arg = xymrw|p|P|c$

    出力の列を作成するために、{x y m r w} のセットから最大5文字を任意の順序で指定します。
  * **N** | **model** :: [Type => Str]      $Arg = [p|P|f|F|c|C|s|S|x]n[,…][+llength][+oorigin][+r]$

    モデルの項数 n_model を指定し、+r を追加してロバストフィットを行います。例: ロバスト二次モデルは -N4+r です。
  * **C** | **condition_number** :: [Type => Number]   $Arg = condition_number$

    行列解のために許可される最大条件数を設定します。
  * **I** | **conf_level** :: [Type => Number | []]   $Arg = [conf_level]$

    モデルパラメータの数を反復的に増加させ、1から始めて n*model に達するか、モデルの分散の減少が conf*level レベルで有意でない場合まで続けます。
  * **W** | **weights** :: [Type => Str | []]     $Arg = [+s]$

    重みは入力列3で提供されます。加重最小二乗フィットを行います [または反復ロバストフィットを行う際にこれらの重みから始めます]。
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

    プライマリ入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを周期的な座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? trend1d$
