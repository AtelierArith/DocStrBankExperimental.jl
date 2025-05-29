```
mbsvplist(cmd0::String=""; kwargs...)
```

スワスソナー データファイル内の水の音速プロファイルをリストします。

## パラメータ

  * **C** | **uniquesvp** :: [Type => Bool]

    各ファイル内のユニークなSVPの数を出力します。
  * **F** | **format** :: [Type => Int]

    入力スワスソナーデータのフォーマットを設定します。
  * **M** | **mode** :: [Type => Int]		$Arg = 1 or 2 or 3$

    SVP出力モードを設定します。
  * **S** | **ssv** :: [Type => Bool]

    入力データで許可される最低速度をkm/hrで設定します（5.5ノット ~ 10 km/hr）。
  * **Z** | **firstiszero** :: [Type => Bool]

    プロットのスタイルを設定します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
