```
istft(stft, samplerate, windowsize, hopsize; window)
```

STFTからマルチチャネルオーディオを再構築します。

# 引数

  * `stft::Array{Complex{T}, 3}`: STFT行列、通常は(1+nfft/2)行を持つ
  * `samplerate::Real`: 結果のオーディオのサンプルレート
  * `windowsize::Int`: STFTに使用されるウィンドウサイズ。(デフォルト: nfft)
  * `hopsize::Int`: STFT列間のフレーム数 (デフォルト: windowsize/4)
  * `nfft::Int`: FFTサイズ (デフォルト: 2*(size(stft,1)-1))
  * `window::Union{Function, AbstractVector, Nothing}`: STFTに使用されるウィンドウの関数またはベクトル (デフォルト: 一様ウィンドウ)
