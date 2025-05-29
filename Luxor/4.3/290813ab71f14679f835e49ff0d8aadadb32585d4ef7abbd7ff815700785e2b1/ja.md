```
placeimage(buffer::AbstractMatrix{ARGB32}, args...;
    kargs...)
```

`pos`で描画にARGB32要素の配列を不透明度/透明度`alpha`で配置します。値は配置される前に「アルファプリマルチプライド」されます。

キーワード`centered=true`を使用して、画像の中心を位置に配置します。
