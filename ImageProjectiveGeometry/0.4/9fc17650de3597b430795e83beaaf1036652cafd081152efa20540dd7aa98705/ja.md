imagecorners2plane - 画像のコーナーを平面に投影した位置を取得します。

```
Usage: pt = imagecorners2plane(C, planeP, planeN)

Arguments:
        C - カメラ構造体または3x4投影行列。
   planeP - 平面上の点を定義する3ベクトル。
   planeN - 平面の法線を定義する3ベクトル。

Returns:
        pt - 画像のコーナーが投影される平面上の3D点の3x4配列。
             点は画像の左上隅から時計回りに並べられます。

```

See also: imagept2plane()
