PSD推定の構造。推定はデフォルトで片側であり、周波数は [0, fₛ/2] の範囲です。

デフォルトの式は

$$
\frac{2|H(f)|^2}{\zeta \sum_i w_i^2}
$$

であり、$w_1, \ldots, w_n$ はハニング窓、$\zeta$ はデフォルトで $1$ の正規化因子です。

バートレット法またはウェルチ法を使用することができ、式は次のようになります。

$$
\frac{1}{M K \varphi} \sum_i^M \left[ \frac{2|H_i(f)|^2}{ \sum_i w_i^2} \right]
$$

ここで、$w_1, \ldots, w_n$ はハニング窓、$M$ はセグメントの数、$K$ はセグメントごとのサンプル数、$H_i(f)$ は信号の$i$番目のセグメントのFFT、$\varphi$ はデフォルトで `1` の正規化因子です。

# フィールド

  * `freq::Vector{<:AbstractFloat}`: スペクトルの周波数範囲
  * `spectrum::Vector{<:AbstractFloat}` : dB単位の推定スペクトル密度。

# コンストラクタ

  * `PSD(x::Vector{<:AbstractFloat}, fs::Integer; window_function::Function = hanning, pad::Integer=0, normalization::Real=1)`: サンプリングレート `fs` の信号 `x` のPSD推定を計算します。信号に `window_function` が適用され、デフォルトはハニング窓です。信号はオプションの長さ `pad` にパディングされる場合があります（デフォルトはゼロ、すなわちパディングなし）。分母には `Real` の `normalization` が追加され、デフォルトは `1` です。
  * `PSD(segs::Vector{Vector{T}}, fs::Integer; window_function=hanning, normalization::Real=1) where {T<:AbstractFloat}`: セグメントベクトル `segs` の平均スペクトルを計算します。推定はデフォルトで $1$ の `normalization` で正規化されます。`window_function` はPSD推定の前にすべてのセグメントに適用されます。

`PSD(x::Vector{<:AbstractFloat}, fs::Integer, seg_length::Integer; overlap::Union{<:AbstractFloat,Integer} = 0.5, window_function::Function=hanning, normalization::Real=1)`: 信号 `x` を長さ `seg_length` のセグメントに分割し、デフォルトで0.5（セグメント長の半分）のオーバーラップを持ちます。信号のセグメンテーション後、結果のセグメントの平均スペクトルが返されます。PSD推定の前にすべてのセグメントに `window_function` が適用され、デフォルトはハニング窓です。最終的な推定はデフォルトで `1` の `normalization` 因子で正規化されます。

  * `PSD(ts::TimeSeries; kargs...)` : TimeSeries信号に最初または2番目のコンストラクタを適用するためのラッパー。
  * `PSD(ts::TimeSeries, seg_length::Integer; kargs...)`: TimeSeries信号に3番目のコンストラクタを適用するためのラッパー。
  * `PSD(freq::Vector{<:AbstractFloat},  spectrum::Vector{<:AbstractFloat})`: 直接コンストラクタ。
