imagept2ray - 画像点に対応する視線を計算します。

```
Usage:  ray = imagept2ray(C, x, y)

Arguments:
         C - カメラ構造、または
             Cは3x4カメラ投影行列であることができます。
      x, y - 画像点 (列, 行)

Returns:
       ray - 画像点に対応する3ベクトル
```

レンズ歪みは、局所的に歪みが一定であると仮定して標準のレンズ歪みパラメータを使用することによって処理され、前方歪みを計算し、その後歪みを引き算します。

関連項目: imagept2ray!(), Camera(), cameraproject()
