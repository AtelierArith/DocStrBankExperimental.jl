undistortimage - 画像からレンズ歪みを除去します

```
Usage 1:  nimg = undistortimage(img, f, ppx, ppy, k1, k2, k3, p1, p2)

Arguments:
         img - 補正する画像。
           f - ピクセル単位での焦点距離
               (focal_length_mm/pixel_size_mm)
    ppx, ppy - ピクセル単位の主点位置。
  k1, k2, k3 - 放射状レンズ歪みパラメータ。
      p1, p2 - 接線レンズ歪みパラメータ。

Usage 2.  nimg = undistortimage(img, camera)

Arguments:
         img - 補正する画像。
         cam - カメラ構造体。

Returns:
         nimg - 補正された画像。
```

放射状および接線歪みパラメータは、投影中心から1単位の画像平面に対応する正規化された画像座標に関して計算/定義されていると仮定されています。これが焦点距離が必要な理由です。
