filter*array*2!(array,smooth*x,smooth*t,position)

入力配列を*インプレース*で移動平均を使用してフィルタリングします。

最初の2次元では、ウィンドウ幅はsmooth*xで、境界は円形として扱われます（2重周期的領域の場合）。空間次元では、幅はsmooth*tで、境界値は複製されます。

この関数は、内部でImages.jlのimfilter関数を呼び出します。
