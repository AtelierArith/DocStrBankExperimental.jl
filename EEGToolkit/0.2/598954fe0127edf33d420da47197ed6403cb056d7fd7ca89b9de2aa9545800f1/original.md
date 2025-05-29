`freq_band(spec::Spectrogram, lower::AbstractFloat, upper::AbstractFloat, window::Integer)`

Given a `Spectrogram`, returns a `Vector{<:AbstractFloat}` with the powers within a frequency band `[lower, upper]` of a specific window (row of the spectrogram).
