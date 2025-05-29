```
fooof_fit(psd, freqs; dims=ndims(psd), min_freq=freqs[1], max_freq=freqs[end], 
          oscillation_peak=true, max_peaks=3)
```

パワースペクトル密度のFOOOFスタイルのフィッティングを実行します。デフォルトの動作は、PLE = 2のローレンツ曲線をフィットすることです。 `allow_variable_exponent=true`の場合、関数は可変PLEのローレンツ曲線をフィットします。

# 引数

  * `psd::AbstractArray{T}`: パワースペクトル密度の値
  * `freqs::Vector{T}`: 周波数の値
  * `dims::Int=ndims(psd)`: 計算を行う次元
  * `min_freq::T=freqs[1]`: 考慮する最小周波数
  * `max_freq::T=freqs[end]`: 考慮する最大周波数
  * `oscillation_peak::Bool=true`: 振動ピークを計算するかどうか
  * `max_peaks::Int=3`: フィットする最大の振動ピーク数
  * `allow_variable_exponent::Bool=false`: 可変指数（PLE）を許可するかどうか
  * `constrained::Bool=false`: 制約付き最適化を使用するかどうか

# 戻り値

`return_only_knee=false`の場合:

  * (knee*frequency, oscillation*parameters)のタプル。ここで、oscillation*parametersは各ピークの(center*freq, amplitude, std_dev)のベクトルです。

`return_only_knee=true`の場合:

  * knee_frequencyのみ

# 注意事項

  * 反復的なFOOOFスタイルのフィッティングを実装します：

    1. 初期ローレンツ曲線をPSDにフィット
    2. ガウスピークを反復的に見つけてフィット
    3. 元のPSDからすべてのガウスを引く
    4. クリーンなPSDにローレンツ曲線を再フィット

```
