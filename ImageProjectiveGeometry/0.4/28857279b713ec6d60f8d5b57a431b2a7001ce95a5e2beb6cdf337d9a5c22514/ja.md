fitplane - 3点以上の点にフィットした平面の係数を解決します

```
Usage:   B = fitplane(XYZ)

Where:   XYZ - 平面にフィットさせるためのxyz座標の3xNpts配列。
               Nptsが3より大きい場合、最小二乗解が生成されます。

Returns: B   - 平面係数の4x1配列で、形式は
               B[1]*X + B[2]*Y + B[3]*Z + B[4] = 0
               Bの大きさは1です。
```

See also: ransacfitplane()
