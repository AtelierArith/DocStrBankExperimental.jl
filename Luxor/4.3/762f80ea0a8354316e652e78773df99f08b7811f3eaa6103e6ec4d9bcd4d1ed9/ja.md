```
readpng(pathname)
```

PNGファイルを読み込みます。

これにより、`placeimage()`を使用して現在の描画に配置するのに適した画像オブジェクトが返されます。`width`および`height`フィールドにアクセスできます：

```
image = readpng("test-image.png")
w = image.width
h = image.height
```
