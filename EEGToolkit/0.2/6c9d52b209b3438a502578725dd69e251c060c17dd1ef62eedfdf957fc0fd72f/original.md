`plot_spectrogram(spec::Spectrogram; freq_lim::AbstractFloat=30.0, type::Int=1, color=:nipy_spectral)`

Plots a spectogram `spec` either in 2d (`type = 1`) or 3d (`type = 2`). An optional  frequency limit (`freq_lim`) may be set (defaults to 30Hz). The color palette  `color` may be set; defaults to `nipy_spectral`.
