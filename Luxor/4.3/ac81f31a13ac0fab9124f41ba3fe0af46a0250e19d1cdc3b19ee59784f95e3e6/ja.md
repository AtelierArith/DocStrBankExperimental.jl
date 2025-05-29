新しい描画を作成し、オプションでファイルタイプ（PNG、PDF、SVG、EPS）、ファイルベースまたはメモリ内、寸法を指定できます。

```
Drawing(width=600, height=600, file="luxor-drawing.png")
```

# 拡張ヘルプ

```julia
Drawing()
```

は描画を作成し、デフォルトでPNG形式、デフォルトのファイル名「luxor-drawing.png」、デフォルトサイズ800ピクセルの正方形になります。

寸法を指定し、デフォルトの出力ファイル名を仮定できます：

```julia
Drawing(400, 300)
```

は400ピクセルの幅と300ピクセルの高さの描画を作成し、デフォルトでPNG形式、デフォルトのファイル名「luxor-drawing.png」にします。

```julia
Drawing(400, 300, "my-drawing.pdf")
```

はファイル「my-drawing.pdf」に400×300ピクセルのPDF描画を作成します。

```julia
Drawing(1200, 800, "my-drawing.svg")
```

はファイル「my-drawing.svg」に1200×800ピクセルのSVG描画を作成します。

```julia
Drawing(width, height, surfacetype | filename)
```

は指定されたサーフェスタイプ（例：:svg、:png）の新しい描画を作成し、ファイル名が提供されていない場合はメモリ内にのみ画像を保存します。

```julia
Drawing(1200, 1200/Base.Mathconstants.golden, "my-drawing.eps")
```

はファイル「my-drawing.eps」に1200ピクセルの幅と741.8ピクセル（= 1200 ÷ ϕ）の高さのEPS描画を作成します。PNGファイルの場合、寸法は整数でなければなりません。

```julia
Drawing("A4", "my-drawing.pdf")
```

はファイル「my-drawing.pdf」にISO A4サイズ（幅595ピクセル、高さ842ピクセル）のPDF描画を作成します。他の利用可能なサイズは「A0」、「A1」、「A2」、「A3」、「A4」、「A5」、「A6」、「Letter」、「Legal」、「A」、「B」、「C」、「D」、「E」です。「landscape」を追加すると横向きバージョンが得られます。

```julia
Drawing("A4landscape")
```

はA4横向きサイズの描画を作成します。

PNGとPDFはデフォルトで透明な背景を持ちますが、`background()`を使用して指定することもできます。

```julia
Drawing(width, height, :image)
```

はメモリ内の画像バッファに描画を作成します。`image_as_matrix()`を使用してデータを行列として取得できます。

```julia
Drawing(width, height, :rec)
```

はメモリ内の記録サーフェスに描画を作成します。`snapshot(fname, ...)`を使用して任意のファイル形式とバウンディングボックスに保存するか、`image_as_matrix()`を使用してピクセルとしてレンダリングします。

```julia
Drawing(width, height, strokescale=true)
```

は描画を作成し、ストロークスケーリングを有効にします（ストロークは現在の変換に応じてスケーリングされます）。 （ストロークスケーリングはデフォルトで無効です。）

```julia
Drawing(img, strokescale=true)
```

は既存の画像バッファ（タイプ`Matrix{Union{RGB24,ARGB32}}`）から描画を作成します。例えば：

```julia
using Luxor, Colors
buffer=zeros(ARGB32, 100, 100)
d=Drawing(buffer)
```
