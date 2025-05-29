```
lines(cmd0::String="", arg1=nothing; decorated=(...), kwargs...)
```

ファイルまたは (x,y) ペアを読み込み、装飾付きの異なるラインのコレクションをプロットします。

  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    マップの境界フレームと軸の属性を設定します。
  * **J** | **proj** | **projection** :: [Type => String]

    マップの投影を選択します。デフォルトは 15x10 cm の線形（非投影）マップです。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **W** | **pen** | **line_attrib** :: [Type => Str]

    ラインまたはシンボルのアウトラインのペン属性を設定します。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図のフォーマットを選択します（例: figname="name.png"）。

例:

```
lines([0, 10]; [0, 20], limits=(-2,12,-2,22), proj="M2.5", pen=1, fill=:red,
	  decorated=(dist=(val=1,size=0.25), symbol=:box), show=true)

lines(x -> cos(x) * x, y -> sin(y) * y, linspace(0,2pi,100), region=(-4,7,-5.5,2.5), lw=2, lc=:sienna,
      decorated=(quoted=true, const_label=" In Vino Veritas  - In Aqua, Rãs & Toads", font=(25,"Times-Italic"),
                 curved=true, pen=(0.5,:red)), aspect=:equal, fmt=:png, show=true)
```
