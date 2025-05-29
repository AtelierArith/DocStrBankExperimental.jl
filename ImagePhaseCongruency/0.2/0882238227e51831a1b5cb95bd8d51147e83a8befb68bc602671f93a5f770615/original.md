Phase congruency of an image using monogenic filters.

This code is considerably faster than `phasecong3()` but you may prefer the output from `phasecong3()`'s oriented filters.

There are potentially many arguments, here is the full usage:

```
  (PC, or, ft, T) =
          phasecongmono(img; nscale, minwavelength, mult,
                        sigmaonf, k, cutoff, g, deviationgain, noisemethod)

However, apart from the image, all parameters have defaults and the
usage can be as simple as:

   (PC,) = phasecongmono(img)   # Use (PC,) so that PC is not a tuple of all
                                # the returned values

More typically you will pass the image followed by a series of keyword
arguments that you wish to set, leaving the remaining parameters set to
their defaults, for example:

   (PC,) = phasecongmono(img, nscale = 5, minwavelength = 3, k = 2.5)

Keyword arguments:
             Default values      Description

   nscale           4    - Number of wavelet scales, try values 3-6
                           A lower value will reveal more fine scale
                           features. A larger value will highlight 'major'
                           features.
   minwavelength    3    - Wavelength of smallest scale filter.
   mult             2.1  - Scaling factor between successive filters.
   sigmaonf         0.55 - Ratio of the standard deviation of the Gaussian
                           describing the log Gabor filter's transfer function
                           in the frequency domain to the filter center frequency.
   k                3.0  - No of standard deviations of the noise energy beyond
                           the mean at which we set the noise threshold point.
                           You may want to vary this up to a value of 10 or
                           20 for noisy images
   cutoff           0.5  - The fractional measure of frequency spread
                           below which phase congruency values get penalized.
   g                10   - Controls the sharpness of the transition in
                           the sigmoid function used to weight phase
                           congruency for frequency spread.
   deviationgain    1.5  - Amplification to apply to the calculated phase
                           deviation result. Increasing this sharpens the
                           edge responses, but can also attenuate their
                           magnitude if the gain is too large.  Sensible
                           values to use lie in the range 1-2.
   noisemethod      -1   - Parameter specifies method used to determine
                           noise statistics.
                             -1 use median of smallest scale filter responses
                             -2 use mode of smallest scale filter responses
                              0+ use noiseMethod value as the fixed noise threshold
                           A value of 0 will turn off all noise compensation.

Returned values:
   PC         - Phase congruency indicating edge significance
   or         - Orientation image in radians -pi/2 to pi/2,  +ve anticlockwise.
                0 corresponds to a vertical edge, pi/2 is horizontal.
   ft         - Local weighted mean phase angle at every point in the
                image.  A value of pi/2 corresponds to a bright line, 0
                corresponds to a step and -pi/2 is a dark line.
   T          - Calculated noise threshold (can be useful for
                diagnosing noise characteristics of images).  Once you know
                this you can then specify fixed thresholds and save some
                computation time.
```

The convolutions are done via the FFT.  Many of the parameters relate to the specification of the filters in the frequency plane.  The values do not seem to be very critical and the defaults are usually fine.  You may want to experiment with the values of `nscales` and `k`, the noise compensation factor.

Typical sequence of operations to obtain an edge image:

```
 > (PC, or) = phasecongmono(img)
 > nm = nonmaxsup(PC, or, 1.5)   # nonmaxima suppression
 > bw = hysthresh(nm, 0.1, 0.3)  # hysteresis thresholding 0.1 - 0.3

Notes on filter settings to obtain even coverage of the spectrum
sigmaonf       .85   mult 1.3
sigmaonf       .75   mult 1.6     (filter bandwidth ~1 octave)
sigmaonf       .65   mult 2.1
sigmaonf       .55   mult 3       (filter bandwidth ~2 octaves)
```

Note that better results are generally achieved using the large bandwidth filters.  I typically use a `sigmaOnf` value of 0.55 or even smaller.

See also:  [`phasecong3`](@ref), [`phasesymmono`](@ref), [`gaborconvolve`](@ref), [`filtergrid`](@ref)
