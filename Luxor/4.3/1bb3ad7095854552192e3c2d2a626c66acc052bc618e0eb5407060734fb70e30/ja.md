```
placeimage(img, pt::Point=O, alpha; centered=false)
placeimage(pngimg, xpos, ypos, alpha; centered=false)
```

PNG画像`pngimg`を位置`pt`または`Point(xpos, ypos)`に不透明度/透明度`alpha`で描画します。画像は以前に`readpng()`を使用して読み込まれています。

キーワード`centered=true`を使用して、画像の中心をその位置に配置します。
