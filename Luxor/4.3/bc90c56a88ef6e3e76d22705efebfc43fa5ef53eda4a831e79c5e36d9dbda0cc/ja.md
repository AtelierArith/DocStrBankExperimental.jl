```
addstop(b::Blend, offset, col)
addstop(b::Blend, offset, (r, g, b, a))
addstop(b::Blend, offset, string)
```

ブレンドにカラー ストップを追加します。オフセットは、ブレンドの「制御ベクトル」に沿った位置を指定し、0（ブレンドの開始）から1（ブレンドの終了）まで変化します。線形ブレンドの場合、制御ベクトルは開始点から終了点までです。放射状ブレンドの場合、制御ベクトルは開始円上の任意の点から、終了円上の対応する点までです。

例:

```
blendredblue = blend(Point(0, 0), 0, Point(0, 0), 1)
addstop(blendredblue, 0, setcolor(sethue("red")..., .2))
addstop(blendredblue, 1, setcolor(sethue("blue")..., .2))
addstop(blendredblue, 0.5, sethue(randomhue()...))
addstop(blendredblue, 0.5, setcolor(randomcolor()...))
```
