スペクトログラムは、$S^{M \times F}$という行列であり、$M$は信号のウィンドウ数、$F$は任意のウィンドウ内のスペクトルベクトルの長さ（すなわち周波数分解能）です。これは、時間におけるスペクトルの変化を観察したり、関心のある時間領域（例えば、睡眠EEGのNREM期間のみ）のスペクトルを計算するのに役立ちます。直接的なPSDから得られる情報は、スペクトログラムから容易に推測できます。

例えば、$f_1, f_2, \ldots, f_k$を厳密に増加する周波数の列とします。これらの周波数が$S$の列インデックス$c_1, c_2, \ldots, c_k$に対応すると仮定します。すると、周波数範囲$[f_1, f_k]$における平均パワーは次のように表されます。

$$
\frac{1}{M} \sum_{i=1}^{M}\left[\frac{1}{c_k - c_1}\sum_{j=c_1}^{c_k} S_{ij}\right] = \frac{1}{M\big(c_k - c_1\big)}\sum_{i=1}^{M}\sum_{j=c_1}^{c_k} S_{ij}
$$

このパッケージでは、周波数範囲における平均パワーは`mean_band_power`関数を使用して計算されます。

# フィールド

  * `time::Vector` : 時間領域
  * `freq::Vector{<:AbstractFloat}`: 周波数領域
  * `spectrums::Matrix{<:AbstractFloat}`: パワースペクトル。行は時間、列は周波数であり、`spectrums[row, freq]`の値は周波数`freq`に対する時間ウィンドウ`row`でのパワーです。
  * `segment_length::Integer` : 各セグメントの時間における長さ。
  * `aggregated_spectra::Vector{<:AbstractFloat}` : スペクトル平均（行の平均）

# コンストラクタ

  * `Spectrogram(segs::Vector{Vector{T}}, psd_function::Function; dB = false) where {T<:AbstractFloat}`: `segs`引数に含まれるウィンドウの列$w_1, \ldots, w_k$に基づいて、カスタム`psd_function`を使用して各ウィンドウ内のPSDを計算します。
  * `Spectrogram(signal::Vector{<:AbstractFloat}, window_length::Integer, psd_function::Function; overlap::Union{AbstractFloat, Integer}=0, dB=false)`: 信号を長さ`window_length`の（重複する可能性のある）セグメントに分割し、最初のコンストラクタを使用してこのウィンドウに対して`Spectrogram`を計算します。各ウィンドウ内でカスタム`psd_function`が使用されます。分割された信号に対して対称性が強制されており、最後のセグメントの長さが他のセグメントと等しくない場合は、それが削除されます。したがって、すべてのウィンドウは同じ長さになります。
  * `function Spectrogram(ts::TimeSeries, window_length::Integer, psd_function::Function; kargs...)`: `TimeSeries`オブジェクトのラッパーコンストラクタです。
