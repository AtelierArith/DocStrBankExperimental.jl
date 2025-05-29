`freq_band(spec::Spectrogram, lower::AbstractFloat, upper::AbstractFloat)`

与えられた `Spectrogram` に対して、すべての時間ウィンドウにわたる周波数帯 [lower, upper] 内のパワーを持つ `Matrix{<:AbstractFloat}` を返します。
