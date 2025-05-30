```
visualize_flow(flow, ColorBased(), RasterConvention())
visualize_flow(flow, ColorBased(), CartesianConvention())
```

入力行列の寸法に一致し、光学フローベクトルの向きと大きさをHSVカラースペースを使用して描写した画像を返します。

# 詳細

色相は画像平面における光学フローベクトルとx軸との間の角度をエンコードし、彩度は個々のベクトルの大きさと全体の運動場の中での最大の大きさとの比率をエンコードし、その値は常に1に等しくなります。

# 引数

flowパラメータは、各ピクセルの変位を表す長さ2のベクトル（SVector型）の二次元配列である必要があります。変位はRasterConvention()（すなわち、行と列の行列）またはCartesianConvention()に基づく座標系で表現できます。

# 例

(row, column)規約でのフローベクトルのHSVエンコードされた視覚化を計算します。

```julia

using ImageTracking

hsv = visualize_flow(flow, ColorBased(), RasterConvention())

imshow(RGB.(hsv))
```

(x, y)規約でのフローベクトルのHSVエンコードされた視覚化を計算します。

```julia

using ImageTracking

hsv = visualize_flow(flow, ColorBased(), CartesianConvention())

imshow(RGB.(hsv))
```

# 参考文献

[1] S. Baker, D. Scharstein, JP Lewis, S. Roth, M.J. Black, and R. Szeliski. A database and evaluation methodology for optical flow. International Journal of Computer Vision, 92(1):1–31, 2011.
