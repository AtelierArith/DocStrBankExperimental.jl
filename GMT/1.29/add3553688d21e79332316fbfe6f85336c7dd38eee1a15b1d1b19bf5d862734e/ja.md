```
bar(cmd0::String="", arg1=nothing; kwargs...)
```

ファイルまたは (x,y) ペアを読み込み、基準から y まで延びる垂直バーをプロットします。

  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは 15x10 cm の線形（非投影）地図です。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **fill** :: [Type => Str –

    バーの塗りつぶしの色またはパターンを選択します。
  * **base** | **bottom** :: [Type => Str | Num]		$key=value$

    デフォルトでは、base = ymin です。このオプションを使用してその値を変更します。base が追加されていない場合は、最後の入力データ列から読み取ります。
  * **size** | **width** :: [Type => Str | Num]		$key=value$

    サイズまたは幅はバーの幅です。サイズが x 単位の場合は u を追加します。*width* が使用される場合、デフォルトはプロット距離単位です。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図の形式を選択します（例：figname="name.png"）。

例:

```
bar(sort(randn(10)), fill=:black, axis=:auto, show=true)
```
