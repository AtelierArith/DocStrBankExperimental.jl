```
FITS_filnam
```

mutable FITSオブジェクトで、`.fits`ファイルの分解された名前を保持します。

フィールドは次の通りです: " `.value`:  `p#.fits`の場合、これは`p#.fits`です（`::String`）

  * `.name`:  `p#.fits`の場合、これは`p#`です（`::String`）
  * `.prefix`:  `p#.fits`の場合、これは`p`です（`::String`）
  * `.numerator`:  `p#.fits`の場合、これは`#`で、シリアル番号（例：'3'）または範囲（例：'3-7'）です（`::String`）
  * `.extension`:  `p#.fits`の場合、これは`.fits`です（`::String`）
