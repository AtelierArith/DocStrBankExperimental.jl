```
placeimage(pngimg, pos=O; centered=false)
placeimage(pngimg, xpos, ypos; centered=false)
```

PNG画像を`pos`または(`xpos`/`ypos`)の位置に描画します。画像`img`は以前に`readpng()`を使用して読み込まれています。

キーワード`centered=true`を使用すると、画像の中心をその位置に配置します。
