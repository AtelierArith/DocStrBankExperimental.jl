```
out = hmin_transform(img, h)
```

深さが h 未満のグレースケール画像のすべての最小値を抑制します。

H-最小値変換は、(img + h) を img によって侵食することによる再構成として定義されます。詳細は Soille の「Morphological image analysis」170-172 ページを参照してください。
