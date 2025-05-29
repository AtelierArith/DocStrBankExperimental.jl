FFTOp(T::Type; shape::Tuple, shift=true, unitary=true)

配列の型 T に対して FFT を実行する演算子を返します。

# 引数:

  * `T::Type`       - 変換する配列の型
  * `shape::Tuple`  - 変換する配列のサイズ
  * (`shift=true`)  - true の場合、fftshifts が実行されます
  * (`unitary=true`)  - true の場合、FFT は単位的になるように正規化されます
  * (`S = Vector{T}`) - 一時的なベクトルの型、GPU で使用するために変更
  * (`kwargs...`) - fft プランに渡されるキーワード引数
