```
DotMatrix(; pixelsize, pixelspacing=pixelsize,
            rounding=zero(pixelsize), meta::Meta=GDSMeta(0,0))
```

# キーワード引数

  * `pixelsize`: 各ピクセルの幅/高さの寸法。
  * `pixelspacing`: 隣接するピクセル間の間隔の寸法。`pixelsize`以上である必要があります。デフォルトは`pixelsize`です。
  * `rounding`: ピクセルの鋭い角のための丸み半径。`pixelsize == pixelspacing`の場合、個々のピクセルは丸められず、ピクセルが結合されて全体の文字が丸められます。
  * `meta`: レイヤー/データ型または類似の情報。
