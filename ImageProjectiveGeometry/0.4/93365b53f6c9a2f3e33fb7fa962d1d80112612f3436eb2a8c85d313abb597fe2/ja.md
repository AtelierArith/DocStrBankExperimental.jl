normalise1dpts - 1D同次点を正規化します

関数は、1D同次点のセットを移動および正規化し、その重心が原点にあり、原点からの平均距離が1になるようにします。

```
Usage:   (newpts, T) = normalise1dpts(pts)

Argument:
  pts -  2xNの1D同次座標の配列

Returns:
  newpts -  2xNの変換された1D同次座標の配列
  T      -  2x2の変換行列、newpts = T*pts
```

無限大にある点の1つがある場合、正規化は不可能です。この場合、警告が表示され、ptsはnewptsとして返され、Tは単位行列になります。

関連項目: normalise2dpts()
