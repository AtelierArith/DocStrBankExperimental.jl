```
spectrogram(waveform;
    pad::Int = 0, n_fft::Int, hop_length::Int, window,
    center::Bool = true, power::Real = 2.0,
    normalized::Bool = false, window_normalized::Bool = false,
)
```

生の音声信号からスペクトログラムまたはスペクトログラムのバッチを作成します。

# 引数

  * `pad::Int`:   両側に適用するパディングの量。
  * `window_normalized::Bool`:   窓のL2エネルギーによって波形を正規化するかどうか。
  * `power::Real`:   大きさのスペクトログラムの指数（≥ 0でなければならない）   例：`1`は大きさ、`2`はパワーなど。   `0`の場合、複素スペクトルが返されます。

他の引数については[`stft`](@ref)を参照してください。

# 戻り値

形状が`(T, F, B)`のスペクトログラム。ここで、`T`はウィンドウホップの数、`F = n_fft ÷ 2 + 1`です。
