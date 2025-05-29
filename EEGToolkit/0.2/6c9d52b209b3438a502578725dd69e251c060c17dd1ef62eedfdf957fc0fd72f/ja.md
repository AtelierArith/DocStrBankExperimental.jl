`plot_spectrogram(spec::Spectrogram; freq_lim::AbstractFloat=30.0, type::Int=1, color=:nipy_spectral)`

スペクトログラム `spec` を2D（`type = 1`）または3D（`type = 2`）でプロットします。オプションの周波数制限（`freq_lim`）を設定できます（デフォルトは30Hz）。カラーパレット `color` を設定できます；デフォルトは `nipy_spectral` です。
