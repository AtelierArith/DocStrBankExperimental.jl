```
clip(cmd0::String="", arg1=nothing; kwargs...)
```

ファイルから (length,azimuth) ペアを読み取り、windclip 図をプロットします。

## パラメータ

  * **C** | **endclip** :: [Type => Bool]

    既存のクリップパスの終わりをマークします。入力ファイルは必要ありません。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは 15x10 cm の線形（非投影）地図です。
  * **A** | **steps** :: [Type => Str or []]

    デフォルトでは、地理的な線分は大円弧として接続されます。直線として接続するには、**A** を使用します。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **N** | **invert** :: [Type => Bool]

    テストの意味を反転させます。すなわち、データカバレッジがあるクリップ領域をクリップします。
  * **P** | **portrait** :: [Type => Bool or []]

    GMT にポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **T** | **clipregion** :: [Type => Bool]

    入力ファイルを読み込むのではなく、現在の地図領域のクリッピングを単にオンにします。

完全なドキュメントを見るには、次のように入力してください: $@? clip$
