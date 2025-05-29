`freq_band(spec::Spectrogram, lower::AbstractFloat, upper::AbstractFloat)`

Given a `Spectrogram`, returns a `Matrix{<:AbstractFloat}` with the powers within a frequency band [lower, upper] across all time windows.
