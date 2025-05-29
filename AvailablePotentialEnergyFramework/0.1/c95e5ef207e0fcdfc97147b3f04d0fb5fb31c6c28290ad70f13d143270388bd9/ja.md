filter*array(array,smooth*x,smooth_t,position)

入力配列を移動平均でフィルタリングします。最初の2次元ではウィンドウ幅はsmooth*xで、境界は円形として扱われます（2重周期的領域の場合）。空間次元では幅はsmooth*tで、境界値は複製されます。

この関数は内部でImages.jlのimfilter関数を呼び出します。

最初の引数は配列と同じサイズのバッファでなければなりません。
