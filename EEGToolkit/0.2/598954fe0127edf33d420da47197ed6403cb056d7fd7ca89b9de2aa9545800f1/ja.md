`freq_band(spec::Spectrogram, lower::AbstractFloat, upper::AbstractFloat, window::Integer)`

与えられた `Spectrogram` に対して、特定のウィンドウ（スペクトログラムの行）の周波数帯 `[lower, upper]` 内のパワーを持つ `Vector{<:AbstractFloat}` を返します。
