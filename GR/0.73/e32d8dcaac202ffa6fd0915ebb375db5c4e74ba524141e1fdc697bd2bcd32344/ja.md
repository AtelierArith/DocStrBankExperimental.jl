```
beginprint(pathname)
```

印刷デバイスを開いてアクティブにします。

**パラメータ:**

`pathname` :     印刷デバイスのファイル名。

`beginprint` は追加のグラフィックス出力デバイスを開きます。デバイスタイプは、指定されたファイル拡張子から取得されます。以下のファイルタイプがサポートされています：

```
+-------------+---------------------------------------+
|.ps, .eps    |PostScript                             |
+-------------+---------------------------------------+
|.pdf         |ポータブルドキュメントフォーマット   |
+-------------+---------------------------------------+
|.bmp         |Windows Bitmap (BMP)                   |
+-------------+---------------------------------------+
|.jpeg, .jpg  |JPEG画像ファイル                       |
+-------------+---------------------------------------+
|.png         |ポータブルネットワークグラフィックスファイル (PNG) |
+-------------+---------------------------------------+
|.tiff, .tif  |タグ付き画像ファイルフォーマット (TIFF) |
+-------------+---------------------------------------+
|.fig         |Xfigベクターグラフィックスファイル    |
+-------------+---------------------------------------+
|.svg         |スケーラブルベクターグラフィックス    |
+-------------+---------------------------------------+
|.wmf         |Windowsメタファイル                   |
+-------------+---------------------------------------+
```
