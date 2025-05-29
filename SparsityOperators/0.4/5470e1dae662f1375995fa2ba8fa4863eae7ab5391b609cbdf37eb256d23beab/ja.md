FFTOp(T::Type, shape::Tuple, shift=true, unitary=true)

配列の型Tに対してFFTを実行する演算子を返します。

# 引数:

  * `T::Type`       - 変換する配列の型
  * `shape::Tuple`  - 変換する配列のサイズ
  * (`shift=true`)  - trueの場合、fftシフトが実行されます
  * (`unitary=true`)  - trueの場合、FFTは単位的になるように正規化されます
