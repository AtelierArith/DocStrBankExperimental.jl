```
filter_array!(buffer,array,smooth_x,smooth_t,position)
```

入力配列を*インプレース*で移動平均を使用してフィルタリングします。最初の2次元ではウィンドウ幅はsmooth*xで、境界は円形として扱われます（2重周期的領域の場合）。空間次元では幅はsmooth*tで、境界値は複製されます。

この関数は、Images.jlのimfilter関数を内部で呼び出します。

最初の引数は、配列と同じサイズのバッファでなければなりません。
