```
visualize_flow(flow, ColorBased(), RasterConvention())
visualize_flow(flow, ColorBased(), CartesianConvention())
```

入力行列の寸法に一致し、光学フロー ベクトルの向きと大きさを HSV カラースペースを使用して描写する画像を返します。

# 詳細

色相は、画像平面における光学フロー ベクトルと x 軸との間の角度をエンコードします。彩度は、個々のベクトルの大きさと全体の運動場の中での最大の大きさとの比率をエンコードし、その値は常に 1 になります。

# 引数

flow パラメータは、各ピクセルの変位を表す長さ 2 のベクトル (SVector 型) の二次元配列である必要があります。変位は、RasterConvention() (すなわち、行と列の行列) または CartesianConvention() に基づく座標系で表現できます。

# 例

(row, column) 形式でのフローベクトルの HSV エンコードされた視覚化を計算します。

```julia

using ImageTracking

hsv = visualize_flow(flow, ColorBased(), RasterConvention())

imshow(RGB.(hsv))
```

(x, y) 形式でのフローベクトルの HSV エンコードされた視覚化を計算します。

```julia

using ImageTracking

hsv = visualize_flow(flow, ColorBased(), CartesianConvention())

imshow(RGB.(hsv))
```

# 参考文献

[1] S. Baker, D. Scharstein, JP Lewis, S. Roth, M.J. Black, and R. Szeliski. A database and evaluation methodology for optical flow. International Journal of Computer Vision, 92(1):1–31, 2011.
