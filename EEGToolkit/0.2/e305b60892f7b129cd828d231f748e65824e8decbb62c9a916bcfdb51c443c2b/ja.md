振幅スペクトル推定の構造。推定はデフォルトで片側であり、周波数は [0, fₛ/2] の範囲です。使用される式は

$$
\frac{2|H(f)|}{\sum_i w_i}
$$

であり、$w_i$ はハニングウィンドウです。

# フィールド

  * `freq::Vector{<:AbstractFloat}`: スペクトルの周波数範囲
  * `spectrum::Vector{<:AbstractFloat}`: 推定されたスペクトル振幅

# コンストラクタ

`AmplitudeSpectrum(x::Vector{<:AbstractFloat}, sampling_rate::Integer, pad::Integer)` : 指定された `sampling_rate` で信号 `x` に対して直接的なPSDを計算します。
