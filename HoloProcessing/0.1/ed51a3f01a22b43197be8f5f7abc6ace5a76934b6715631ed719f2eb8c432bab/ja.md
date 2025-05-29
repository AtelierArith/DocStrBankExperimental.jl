rse(     holo::AbstractMatrix{T},      windows_size::Tuple{Integer,Integer},      interval::Tuple{Integer,Integer},      P::FFTW.FFTWPlan,      scale::Integer;      shift = false     ) -> AbstractMatrix{T} where T <: AbstractFloat

`冗余散斑降噪法`のアルゴリズム実装、具体的には`doi: 10.1364/AO.390500`を参照してください。

# 引数

  * holo: 全息図（非RGBタイプではなくAbstractFloatタイプ）
  * windows_size: マスクウィンドウのサイズ
  * interval: ウィンドウのオフセット
  * holo: 元の全息図
  * P: FFTW.FFTWPlan型で、再構築に`fft`フーリエ変換を使用することを示します
  * scale: ゼロ次像の強度が大きすぎるため、±1次像の強度を`scale`で引き上げる必要があります
  * shift: 画像を回転させるかどうか、デフォルトはいいえ（完全な再構築像を表示したい場合を除き、`shift`を`true`に設定することはお勧めしません。なぜなら、メモリと時間のコストが大きいためです）
