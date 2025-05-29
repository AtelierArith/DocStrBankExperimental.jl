Computes edge and corner phase congruency in an image via log-Gabor filters.

There are potentially many arguments, here is the full usage:

```
  (M, m, or, ft, EO, T) = phasecong3(img; nscale, norient, minwavelength,
                          mult, sigmaonf, k, cutoff, g, noisemethod)
```

However, apart from the image, all parameters have defaults and the usage can be as simple as:

```
    (M,) = phasecong3(img)

Keyword Arguments:
             Default values      Description

   nscale           4    - Number of wavelet scales, try values 3-6
   norient          6    - Number of filter orientations.
   minwavelength    3    - Wavelength of smallest scale filter.
   mult             2.1  - Scaling factor between successive filters.
   sigmaonf         0.55 - Ratio of the standard deviation of the Gaussian
                           describing the log Gabor filter's transfer function
                           in the frequency domain to the filter center frequency.
   k                2.0  - No of standard deviations of the noise energy beyond
                           the mean at which we set the noise threshold point.
                           You may want to vary this up to a value of 10 or
                           20 for noisy images
   cutoff           0.5  - The fractional measure of frequency spread
                           below which phase congruency values get penalized.
   g                10   - Controls the sharpness of the transition in
                           the sigmoid function used to weight phase
                           congruency for frequency spread.
   noisemethod      -1   - Parameter specifies method used to determine
                           noise statistics.
                             -1 use median of smallest scale filter responses
                             -2 use mode of smallest scale filter responses
                              0+ use noisemethod value as the fixed noise threshold

Returned values:
   M          - Maximum moment of phase congruency covariance.
                This is used as a indicator of edge strength.
   m          - Minimum moment of phase congruency covariance.
                This is used as a indicator of corner strength.
   or         - Orientation image in radians -pi/2 to pi/2,  +ve anticlockwise.
                0 corresponds to a vertical edge, pi/2 is horizontal.
   ft         - Local weighted mean phase angle at every point in the
                image.  A value of pi/2 corresponds to a bright line, 0
                corresponds to a step and -pi/2 is a dark line.
   EO         - A 2D array of complex valued convolution results for each scale
                and orientation
   T          - Calculated noise threshold (can be useful for
                diagnosing noise characteristics of images).  Once you know
                this you can then specify fixed thresholds and save some
                computation time.
```

`EO[s,o]` = convolution result for scale `s` and orientation `o`.  The real part is the result of convolving with the even symmetric filter, the imaginary part is the result from convolution with the odd symmetric filter.

Hence:       `abs.(EO[s,o])` returns the magnitude of the convolution over the       image at scale `s` and orientation `o`,       `angle.(EO[s,o])` returns the phase angles.

The convolutions are done via the FFT.  Many of the parameters relate to the specification of the filters in the frequency plane.  The values do not seem to be very critical and the defaults are usually fine.  You may want to experiment with the values of `nscales` and `k`, the noise compensation factor.

Some filter parameters to obtain even coverage of the spectrum

```
sigmaonf       .85   mult 1.3
sigmaonf       .75   mult 1.6     (filter bandwidth ~1 octave)
sigmaonf       .65   mult 2.1
sigmaonf       .55   mult 3       (filter bandwidth ~2 octaves)
```

See also:  [`phasesym`](@ref), [`gaborconvolve`](@ref)
