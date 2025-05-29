phonspec(s, fs; pre_emph=0.97, dbr=55, win=:gaussian, 			winparam=nothing, winlen=0.005, winstep=0.002, kw...)

Rudimentary functionality to plot a spectrogram, with parameters familiar to phoneticians. Includes a pre-emphasis routine which helps increase the intensity of the higher frequencies in the display. Defaults to a Gaussian window with a standard deviation of 1/6.

For a **broadband** spectrogram, use a value around 0.005 for `winlen`. For a **narrowband** spectrogram, use a value around 0.03 for `winlen`.

Argument structure inferred from using plot recipe. Parameters such as `xlim`, `ylim`, `color`, and `size` should be passed as keyword arguments, as with standard calls to `plot`.

# Args

  * `s` A vector containing the samples of a sound
  * `fs` Sampling frequency of `s` in Hz
  * `pre_emph` The α coefficient for pre-emmphasis; default value of 0.97 corresponds to a cutoff frequency of approximately 213 Hz before the 6 dB / octave increase begins
  * `dbr` The dynamic range; all frequencies that are `dbr` decibels quieter than the loudest frequency will not be displayed; will specify the `clim` argument
  * `win` The type of window to use; must be one of `:gaussian` or `:kaiser`
  * `winparam` The parameter affecting the scale of the window; if nothing passed, uses 1/6 for a Gaussian window or 3 for a Kaiser window
  * `winlen` The length of the window in seconds (note that this value gets doubled in the code)
  * `winstep` How far apart each window is in seconds
  * `kw...` extra named parameters to pass to `heatmap`
