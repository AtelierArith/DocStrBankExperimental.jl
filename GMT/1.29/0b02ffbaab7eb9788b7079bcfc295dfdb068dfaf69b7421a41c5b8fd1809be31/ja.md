```
makecpt(cmd0::String="", arg1=nothing; kwargs...)
```

または

```
makecpt(name::Symbol; kwargs...)
```

静的なカラーパレットテーブル（CPT）を作成します。2番目の形式は、GMT CPTのデフォルトの1つの名前を受け入れます。

  * **A** | **alpha** | **透明度** :: [Type => Str]

    すべてのカラースライスに対して一定の透明度レベル（0-100）を設定します。
  * **C** | **color** | **カラーマップ** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT名を指定するか、-Ccolor1,color2[,color3,...]を指定して、これらの色から自動的に線形連続CPTを構築します。
  * **D** | **bg** | **背景** :: [Type => Str | []]			`Arg = [i|o]`

    出力CPTの最小および最大z値に一致する前景および背景色を選択します。
  * **E** | **nlevels** :: [Type => Int | []]		`Arg = [nlevels]`

    ファイルまたは配列からデータテーブルを読み取ることを示唆します。データ範囲を決定するために最後のデータ列を使用します。
  * **F** | **color_model** :: [Type => Str | []]		`Arg = [R|r|h|c][+c]]`

    出力CPTをr/g/bコード、グレースケール値、または色名で書き込むよう強制します。
  * **G** | **truncate** :: [Type => Str]              `Arg = zlo/zhi`

    入力CPTを切り捨てて、最小および最大zレベルをzloおよびzhiにします。
  * **I** | **inverse** | **reverse** :: [Type => Str]	`Arg = [c][z]`

    マスターCPTの色の進行方向を逆にします。
  * **M** | **overrule_bg** :: [Type => Bool]

    マスターCPTで指定された背景、前景、およびNaN色を、パラメータCOLOR*BACKGROUND、COLOR*FOREGROUND、およびCOLOR_NANの値で上書きします。
  * **N** | **no_bg** | **nobg** :: [Type => Bool]

    背景、前景、およびNaN色フィールドを書き出さないようにします。
  * **Q** | **log** :: [Type => Bool | Str]			`Arg = [i|o]`

    対数補間スキームを選択します [デフォルトは線形]。
  * **S** | **auto** :: [Type => Bool | Str]			`Arg = [mode]`

    入力テーブル（またはstdin）から-Tオプションに適した範囲を決定します。
  * **T** | **range** :: [Type => Str]			`Arg = [min/max/inc[+b|l|n]|file|list]`

    最小および最大z値と間隔を指定することによって、新しいCPTの範囲を定義します。
  * **W** | **wrap** | **categorical** :: [Type => Bool | Str | []]      `Arg = [w]`

    入力カラーテーブルを補間せず、カラーテーブルの最初から出力色を選択し、すべての間隔に色が割り当てられるまで続けます。
  * **Z** | **continuous** :: [Type => Bool]

    連続CPTを作成します [デフォルトは不連続、すなわち各間隔に対して一定の色]。

完全なドキュメントを見るには、次のように入力してください: $@? makecpt$
