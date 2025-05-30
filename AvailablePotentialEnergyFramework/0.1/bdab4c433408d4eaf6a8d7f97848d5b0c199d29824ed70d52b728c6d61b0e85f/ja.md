```
filter_array_2!(array,smooth_x,smooth_t,position)
```

入力配列を*インプレース*で移動平均を使用してフィルタリングします。

最初の2次元ではウィンドウ幅はsmooth*xで、境界は円形として扱われます（2重周期的領域の場合）。空間次元では幅はsmooth*tで、境界値は複製されます。

この関数は、内部でImages.jlのimfilter関数を呼び出します。
