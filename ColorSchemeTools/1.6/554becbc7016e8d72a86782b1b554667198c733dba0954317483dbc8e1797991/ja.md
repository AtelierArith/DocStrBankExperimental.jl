```
image_to_swatch(imagefilepath, samples, destinationpath;
    nrows=50,
    tilewidth=5)
```

`imagefilepath`の画像からカラースキームを抽出し、`destinationpath`にスウォッチ画像PNGとして保存します。これは、`sortcolorscheme()`、`colorscheme_to_image()`、および`save()`を順に実行するだけです。

色の数を指定します。また、行数や各色の繰り返し回数を指定することもできます。

```
image_to_swatch("monalisa.jpg", 10, "/tmp/monalisaswatch.png")
```
