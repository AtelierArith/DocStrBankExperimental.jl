solvestereopt - ステレオポイントの同次線形解

```
使用法:
        pt = solvestereopt(xy, P)
        pt = solvestereopt(xy, C)
        (pt, xy_reproj) = solvestereopt(xy, P, reprojecterror=true)
        (pt, xy_reproj) = solvestereopt(xy, C, reprojecterror=true)

マルチビューステレオ: 2つ以上の画像におけるその点の画像座標から、点の3D位置を解決します。

引数:        xy - x, y画像座標の2xN行列、各カメラごとに1列。
               P - 対応する3x4画像投影行列のN配列、または
               C - カメラ構造体のN配列
  reprojecterror - 再投影誤差を返すべきかどうかを示すブールフラグ。

返り値:      pt - 正規化された同次座標で返される空間内の3D位置
                   （最後の要素 = 1の4ベクトル）
       xy_reproj - 再投影された画像座標の2xN行列。
```

参照: idealimagepts(), camstruct2projmatrix(), Camera()
