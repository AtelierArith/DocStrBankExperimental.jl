```
grd2cpt(cmd0::String="", arg1=nothing, kwargs...)
```

グリッドから線形またはヒストグラム均等化されたカラーパレットテーブルを作成します

## パラメータ

  * **A** | **alpha** | **透明度** :: [Type => Str]

    すべてのカラースライスに対して一定の透明度レベル（0-100）を設定します。
  * **C** | **color** | **カラーマップ** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT名を指定するか、-Ccolor1,color2[,color3,...]を指定して、これらの色から自動的に線形連続CPTを構築します。
  * **D** | **bg** | **背景** :: [Type => Str | []]			`Arg = [i|o]`

    出力CPTの最小および最大z値に一致する前景および背景色を選択します。
  * **E** | **nlevels** :: [Type => Int | []]		`Arg = [nlevels]`

    グリッドz範囲を新しいCPTの制限として使用して線形カラーテーブルを作成します。 あるいは、nlevelsを追加すると、カラーテーブルをnlevelsの等間隔スライスに再サンプリングします。
  * **F** | **color_model** :: [Type => Str | []]		`Arg = [R|r|h|c][+c]]`

    出力CPTをr/g/bコード、グレースケール値、または色名で書き込むよう強制します。
  * **G** | **truncate** :: [Type => Str]             `Arg = zlo/zhi`

    入力CPTを切り詰めて、最小および最大zレベルをzloおよびzhiに設定します。
  * **I** | **inverse** | **reverse** :: [Type => Str]	    `Arg = [c][z]`

    マスターCPTの色の進行方向を逆にします。
  * **L** | **datarange** | **clim** :: [Type => Str]			`Arg = minlimit/maxlimit`

    CPTの範囲をminlimit/maxlimitに制限し、この範囲外のデータをCDF(Z)の推定にカウントしません。   [デフォルトはデータの最小値と最大値を使用します。]
  * **M** | **overrule_bg** :: [Type => Bool]

    マスターCPTで指定された背景、前景、およびNaN色を、パラメータCOLOR*BACKGROUND、COLOR*FOREGROUND、およびCOLOR_NANの値で上書きします。
  * **N** | **no_bg** | **nobg** :: [Type => Bool]

    背景、前景、およびNaN色フィールドを書き出しません。
  * **Q** | **log** :: [Type => Bool]

    対数補間スキームを選択します [デフォルトは線形です]。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。 提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **S** | **symmetric** :: [Type => Str]			`Arg = h|l|m|u`

    カラーテーブルをゼロを中心に対称にします（-Rから+Rまで）。
  * **T** | **range** :: [Type => Str]			`Arg = (min,max,inc) or = "n"`

    CPTのステップを設定します。 zstartからzstopまでのCPTのエントリを(zinc)のステップで計算します。 デフォルトは、ガウスCDFの等間隔値に基づく奇妙なスキームによって任意の値を選択します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗レポートをstderrに送信する冗長性レベルを選択します。
  * **W** | **categorical** :: [Type => Bool | Str | []]      `Arg = [w]`

    入力カラーテーブルを補間せず、カラーテーブルの最初から出力色を選択し、すべての区間に色が割り当てられるまで続けます。
  * **Z** | **continuous** :: [Type => Bool]

    連続CPTを作成します [デフォルトは不連続、すなわち各区間に対して一定の色です]。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗レポートをstderrに送信する冗長性レベルを選択します。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に返すのではなく、ASCIIファイルに保存します。 ファイル名を引数として指定します。   boオプションを使用してバイナリファイルとして保存します。

完全なドキュメントを見るには、次のように入力します: $@? grd2cpt$ ```
