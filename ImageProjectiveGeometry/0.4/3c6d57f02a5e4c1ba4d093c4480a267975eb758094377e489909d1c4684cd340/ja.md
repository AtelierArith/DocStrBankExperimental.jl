idealimagepts - 理想的な画像点で、歪みがありません。

```
Usage:  xyideal = idealimagepts(C, xy)

Arguments:
         C - カメラ構造
        xy - 2 x N 配列 (x,y) / (列,行) で指定された画像点

Returns:
   xyideal - 理想的な画像点。これらの点は、カメラにレンズ歪みがなかった場合に得られる画像
             の位置に対応します。つまり、fx, fy, ppx, ppy, skew から計算された理想的な
             投影行列を使用して投影された場合の点です。
```

See also Camera(), cameraproject()
