```
imview(img; clims=Percent(99.5), stretch=identity, cmap=:magma, contrast=1.0, bias=0.5)
```

配列またはAstroImageMatの読み取り専用ビューを作成し、そのデータ値を`clims`、`stretch`、および`cmap`に従って色にマッピングします。

データは最初に`clims`にクランプされます。`clims`は(min, max)値のタプルまたはピクセル値のイテレータを受け取り(min, max)を返す関数のいずれかです。デフォルトでは、`clims=Percent(99.5)`で、ピクセル値の中央99.5パーセンタイル範囲に表示の最小値と最大値を設定します。`clims`に便利な関数には、`extrema`、`Zscale`、および`Percent(p)`があります。

次に、データは[0,1]に再スケーリングされ、関数`stretch`に従って再マッピングされます。Stretchは、範囲[0,1]の値をある範囲[a,b]にマッピングする任意の単調関数であることができます。`log(0)`は定義されていないため、直接サポートされていません。便利なストレッチ関数のリストについては、`logstretch`、`powstretch`、`squarestretch`、`asinhstretch`、`sinhstretch`、`powerdiststretch`を参照してください。

最後に、データは`cmap`に従ってRGB値にマッピングされます。cmapが`nothing`の場合、グレースケールが使用されます。ColorSchemes.jlは数百のカラーマップを定義しています。画像に適したいくつかの良いものには、`:viridis`、`:magma`、`:plasma`、`:thermal`、および`:turbo`があります。

重要なことに、この関数は基になるデータに対するビューを返します。`img`が更新されると、その変更はこのビューに反映されますが、`clims`は再計算されません。

注意: `clims`または`stretch`が関数の場合、渡されたピクセル値は最初にフィルタリングされ、非有限または欠損値が削除されます。

### デフォルト

`clims`、`stretch`、および`cmap`のデフォルト値はそれぞれ`extrema`、`identity`、および`nothing`です。これらのデフォルトは、`AstroImages.set_clims!`、`AstroImages.set_stretch!`、および`AstroImages.set_cmap!`を使用して変更できます。

### 自動表示

`AstroImageMat()`でラップされた配列は、PNG画像を表示することをサポートするディスプレイを使用する際に、デフォルト設定で`imview`を呼び出すことで自動的に画像として表示されます。

### 欠損データ

`NaN`または`missing`のピクセルは、`cmap`が設定されている場合は透明として表示され、そうでない場合は黒として表示されます。+/- Infはそれぞれ黒または白として表示されます。

### 画像のエクスポート

`imview`によって返されたビューは、一般的な`FileIO.save`メソッドを使用して保存できます。例:

```julia
v = imview(data, cmap=:magma, stretch=asinhstretch, clims=Percent(95))
save("output.png", v)
```
