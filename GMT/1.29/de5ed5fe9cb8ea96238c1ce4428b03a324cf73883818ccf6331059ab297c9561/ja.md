```
psconvert(cmd0::String="", arg1=nothing; kwargs...)
```

地図上に画像またはEPSファイルを配置します。

## パラメータ

  * **A** | **adjust** | **crop** :: [Type => Str or Number]  

    画像コンテンツに必要な最小限のBoundingBoxとHiResBoundingBoxを調整します。
  * **C** | **gs_option** :: [Type => Str or Array os strings]

    GhostScriptにそのまま渡されるカスタムオプションの単一または配列を指定します。
  * **D** | **out_dir** | **output_dir** :: [Type => Str]

    代替出力ディレクトリを設定します（存在する必要があります）[デフォルトはPSファイルと同じディレクトリです]。
  * **E** | **dpi** :: [Type => Number]

    dpiでラスタ解像度を設定します [デフォルト = PDFの場合は720、その他の場合は300]。
  * **F** | **:out_name** | **output_name** :: [Type => Str]

    出力ファイル名を強制します。
  * **G** | **ghost_path** :: [Type => Bool]

    GhostScript実行可能ファイルへのフルパス。
  * **I** | **resize** :: [Type => Bool]

    スケーリングおよび/またはマージンを追加することによってBoundingBoxとHiResBoundingBoxを調整します。
  * **in_memory** :: [Type => Bool]

    メモリ内のPSファイルを処理します。他の入力ファイルは提供されるべきではありません。 現在はWindowsでのみ動作します。
  * **L** | **list_file** :: [Type => Str]

    listfileは、変換されるPostScriptファイルの名前を含むASCIIファイルです。
  * **M** | **embed**

    現在のpsfileをオプションの背景（-Mb）とオプションの前景（-Mf）Postscriptプロットの間に挟みます。
  * **N** | **bgcolor**

    オプションのBoundingBox背景塗りつぶし色、フェード、またはBoundingBoxのアウトラインを描画します。
  * **Q** | **anti_aliasing** :: [Type => Str]

    グラフィックスまたはテキストのアンチエイリアスオプションを設定します。サブサンプルボックスのサイズ（1、2、または4）を追加します [4]。このオプションはデフォルトで設定されています。
  * **S** | **gs_command** :: [Type => Bool]

    GhostScriptコマンドが実行された後、標準エラーに印刷します。
  * **T** | **format** :: [Type => Str]

    b|e|E|f|F|j|g|G|m|s|t 出力形式を設定します。ここでb = BMP、e = EPS、E = PageSizeコマンド付きEPS、f = PDF、F = マルチページPDF、j = JPEG、g = PNG、G = 透明PNG（未処理の領域は透明）、m = PPM、t = TIFF [デフォルトはJPEG]です。 また、形式は*fmt*キーワードで設定することもできます。例：*fmt=:png*。
  * **W** | **world_file** :: [Type => Str]

    ソフトウェアがそれを認識できるように、（例：）.tifファイルをgeotiffとして作成するのに適したESRIタイプのワールドファイルを書き込みます。
  * **kml** :: [Type => Str | []]

    GoogleEarthで画像を読み込むことを可能にするミニマリストKMLファイルを作成します。
  * **Z** | **del*input*ps** :: [Type => Bool]

    変換後に入力PostScriptファイルを削除します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。

完全なドキュメントを見るには、次のように入力します: $@? psconvert$
