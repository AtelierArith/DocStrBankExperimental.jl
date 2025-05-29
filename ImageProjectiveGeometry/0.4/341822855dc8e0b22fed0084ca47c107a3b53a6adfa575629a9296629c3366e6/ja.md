fitline3d - 3Dポイントのセットに線をフィットさせる

```
Usage:   L = fitline3d(XYZ)

Where: XYZ - 3xNptsのXYZ座標の配列
              [x1 x2 x3 ... xN;
               y1 y2 y3 ... yN;
               z1 z2 z3 ... zN]

Returns: L - 点にフィットする線の2つの端点からなる3x2行列
             この線は点の平均を中心にし、主固有ベクトルの方向に
             拡張され、スケールは固有値によって決まります。
```
