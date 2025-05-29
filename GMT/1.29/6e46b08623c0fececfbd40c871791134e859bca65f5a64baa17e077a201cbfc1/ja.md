```
mbgetdata(cmd0::String=""; kwargs...)
```

バシメトリ、サイドスキャン、または振幅データをデータファイルから抽出します。

## パラメータ

  * **A** | **flagged** :: [Type => Number]	$Arg = value$

    フラグが付けられたビーンをNaNで置き換えます。-A<val>を使用して、フラグが付けられたビーンに定数値を割り当てます。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **C** | **datatype** | **data_type** :: [Type => Number | Str | Tuple]	$Arg = 0 or "a"$

    バシメトリの代わりにサイドスキャンまたは振幅を出力します。この場合、**A**は無視されます。
  * **D** | **scaling** :: [Type => Str | Tuple]	$Arg = <mode>/<ampscale>/<ampmin>/<ampmax>$

    プロット前に適用できるビーム振幅またはサイドスキャンピクセル値のスケーリングを設定します。
  * **F** | **format** :: [Type => Int]

    MBIO整数形式識別子を使用して、入力スワスソナーのデータ形式を設定します。
  * **S** | **speed** :: [Type => Number]

    バシメトリのシミュレートされた照明を制御するパラメータを設定します。
  * **T** | **timegap** :: [Type => number]

    隣接するピング間の最大時間ギャップを分単位で設定します。ギャップと見なされる前の時間ギャップです。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのためにbを追加することでグリッド補間モードを選択します。cはバイキュービック補間、lはバイリニア補間、nは最近傍値を示します。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]です。
