Apply monogenic filters to an image to obtain 2D analytic signal.

This is an implementation of Felsberg's monogenic filters

```
Usage: (f, h1f, h2f, A, theta, psi) =
            monofilt(img, nscale, minWaveLength, mult, sigmaOnf, orientWrap)
                             3         4           2     0.65    true/false
Arguments:
The convolutions are done via the FFT.  Many of the parameters relate
to the specification of the filters in the frequency plane.

  Variable       Suggested   Description
  name           value
 ----------------------------------------------------------
   img                       Image to be convolved. An Array of Real or Gray.
   nscale          = 3       Number of filter scales.
   minWaveLength   = 4       Wavelength of smallest scale filter.
   mult            = 2       Scaling factor between successive filters.
   sigmaonf        = 0.65    Ratio of the standard deviation of the
                             Gaussian describing the log Gabor filter's
                             transfer function in the frequency domain
                             to the filter center frequency.
   orientWrap       false    Optional Boolean flag  to turn on/off
                             'wrapping' of orientation data from a
                             range of -pi .. pi to the range 0 .. pi.
                             This affects the interpretation of the
                             phase angle - see note below. Defaults to false.
Returns:
       f  - vector of bandpass filter responses with respect to scale.
     h1f  - vector of bandpass h1 filter responses wrt scale.
     h2f  - vector of bandpass h2 filter responses.
       A  - vector of monogenic energy responses.
   theta  - vector of phase orientation responses.
     psi  - vector of phase angle responses.
```

If `orientWrap` is true `theta` will be returned in the range `0 .. pi`

Experimentation with `sigmaonf` can be useful depending on your application. I have found values as low as 0.2 (a filter with a *very* large bandwidth) to be useful on some occasions.

See also: [`gaborconvolve`](@ref)
