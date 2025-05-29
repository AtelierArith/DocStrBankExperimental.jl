```
subplot(fim=nothing; kwargs...)
```

図のサブプロット設定と選択を管理します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`subplot`](http://docs.generic-mapping-tools.org/latest/subplot.html)を参照してください。

## パラメータ

  * **grid** :: [Type => Str | Tuple | Array]

    サブプロットの行数と列数を指定します。例: grid=(2,3)
  * **F** | **dims** | **dimensions** | **size** | **sizes** :: [Type => Str | Tuple, NamedTuple]

    図の寸法を指定します。
  * **A** | **autolabel** | **fixedlabel** :: [Type => Str | number]

    各サブプロットの自動タグ付けを指定します。これにより、最初の左上のサブプロットのタグが設定され、他のサブプロットは順次続きます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **clearance** :: [Type => Str | number]

    指定された側のマージンとサブプロットの間にクリアランスの寸法のスペースを確保します。**begin**ディレクティブの下で指定された設定はすべてのパネルに適用されます。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **M** | **margin** | **margins** :: [Type => Str]

    各サブプロットの周りに追加されるマージンスペースで、目盛り、注釈、ラベルのために自動的に割り当てられたスペースを超えます。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **SC** | **SR** | **col_axes** | **row_axes** :: [Type => Str | NamedTuple]

    共有軸のためのサブプロットレイアウトを設定します。行（SR）と列（SC）ごとに別々に設定します。
  * **T** | **title** :: [Type => Str]

    各サブプロットにはタイトルを付けることができますが、全体の図にも包括的なタイトルを付けることができます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さの単位（c, i, または p）を追加します。
