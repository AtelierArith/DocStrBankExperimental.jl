```
ldr(
    holo::AbstractMatrix{T}, 
    N::Integer, 
    interval::Tuple{Integer,Integer}, 
    P::FFTW.FFTWPlan, 
    scale::Integer; 
    shift = false
    ) -> AbstractMatrix{T} where T <: AbstractFloat
```

`低次元再構成法`のアルゴリズム実装、詳細は`doi: 10.1364/AO.414773`を参照

# 引数

  * holo: ホログラム
  * N: ウィンドウサイズの`N`倍は`holo`のサイズに等しい
  * interval: ウィンドウのオフセット
  * holo: 元のホログラム
  * P: FFTW.FFTWPlan型で、再構成に`fft`フーリエ変換を使用することを示す
  * scale: ゼロ次像の強度が大きすぎるため、±1次像の強度を`scale`で引き上げる必要がある
  * shift: 画像を回転させるかどうか、デフォルトは否（完全な再構成像を表示したい場合を除き、`shift`を`true`に設定することは推奨されない、なぜならそのメモリと時間のコストが大きいため）
