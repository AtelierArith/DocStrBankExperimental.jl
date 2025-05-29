Phase symmetry of an image using monogenic filters.

This function calculates the phase symmetry of points in an image. This is a contrast invariant measure of symmetry.  This function can be used as a line and blob detector.  The greyscale polarity of the lines that you want to find can be specified.

This code is considerably faster than `phasesym()` but you may prefer the output from `phasesym()`'s oriented filters.

There are potentially many arguments, here is the full usage:

```
  (phSym, symmetryEnergy, T) =
               phasesymmono(img; nscale, minwaveLength, mult,
                            sigmaonf, k, polarity, noisemethod)
```

However, apart from the image, all parameters have defaults and the usage can be as simple as:

```
   (phSym,) = phasesymmono(img)

Keyword arguments:
             Default values      Description

   nscale           5    - Number of wavelet scales, try values 3-6
   minwaveLength    3    - Wavelength of smallest scale filter.
   mult             2.1  - Scaling factor between successive filters.
   sigmaonf         0.55 - Ratio of the standard deviation of the Gaussian
                           describing the log Gabor filter's transfer function
                           in the frequency domain to the filter center frequency.
   k                2.0  - No of standard deviations of the noise energy beyond
                           the mean at which we set the noise threshold point.
                           You may want to vary this up to a value of 10 or
                           20 for noisy images
   polarity         0    - Controls 'polarity' of symmetry features to find.
                            1 - just return 'bright' points
                           -1 - just return 'dark' points
                            0 - return bright and dark points.
   noisemethod      -1   - Parameter specifies method used to determine
                           noise statistics.
                             -1 use median of smallest scale filter responses
                             -2 use mode of smallest scale filter responses
                              0+ use noiseMethod value as the fixed noise threshold
                           A value of 0 will turn off all noise compensation.

Return values:
   phSym                 - Phase symmetry image (values between 0 and 1).
   symmetryEnergy        - Un-normalised raw symmetry energy which may be
                           more to your liking.
   T                     - Calculated noise threshold (can be useful for
                           diagnosing noise characteristics of images)
```

The convolutions are done via the FFT.  Many of the parameters relate to the specification of the filters in the frequency plane.  The values do not seem to be very critical and the defaults are usually fine.  You may want to experiment with the values of `nscales` and `k`, the noise compensation factor.

Notes on filter settings to obtain even coverage of the spectrum

```
sigmaonf       .85   mult 1.3
sigmaonf       .75   mult 1.6     (filter bandwidth ~1 octave)
sigmaonf       .65   mult 2.1
sigmaonf       .55   mult 3       (filter bandwidth ~2 octaves)
```

See Also:  [`phasesym`](@ref), [`phasecongmono`](@ref)
