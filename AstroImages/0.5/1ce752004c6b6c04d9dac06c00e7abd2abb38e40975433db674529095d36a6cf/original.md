```
polquiver(polqube::AstroImage)
```

Given a data cube (of at least 2 spatial dimensions, plus a polarization axis), plot a vector field of polarization data. The tick length represents the polarization intensity, sqrt(q^2 + u^2), and the color represents the linear polarization fraction, sqrt(q^2 + u^2) / i.

There are several ways you can adjust the appearance of the plot using keyword arguments:

  * `bins` (default = 1) By how much should we bin down the polarization data before drawing the ticks? This reduced clutter from higher resolution datasets. Can be fractional.
  * `ticklen` (default = bins) How long the 98th percentile arrow should be. By default, 1 bin long. Make this larger to draw longer arrows.
  * `color` (default = :turbo) What colorscheme should be used for linear polarization fraction.
  * `minpol` (default = 0.2) Hides arrows that are shorter than `minpol` times the 98th percentile arrow to make a cleaner image. Set to 0 to display all data.

Use `implot` and `polquiver!` to overplot polarization data over an image.
