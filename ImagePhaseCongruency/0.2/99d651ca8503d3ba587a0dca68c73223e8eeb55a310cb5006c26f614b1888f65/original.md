Convolve an image with a bank of log-Gabor filters.

```
Usage: (EO, BP) = gaborconvolve(img,  nscale, norient, minWaveLength, mult,
                                 sigmaOnf, dThetaOnSigma, Lnorm)

Arguments:
The convolutions are done via the FFT.  Many of the parameters relate
to the specification of the filters in the frequency plane.

  Variable       Suggested   Description
  name           value
 ----------------------------------------------------------
   img                       Image to be convolved.
   nscale          = 4       Number of wavelet scales.
   norient         = 6       Number of filter orientations.
   minWaveLength   = 3       Wavelength of smallest scale filter.
   mult            = 1.7     Scaling factor between successive filters.
   sigmaOnf        = 0.65    Ratio of the standard deviation of the
                             Gaussian describing the log Gabor filter's
                             transfer function in the frequency domain
                             to the filter center frequency.
   dThetaOnSigma   = 1.3     Ratio of angular interval between filter
                             orientations and the standard deviation of
                             the angular Gaussian function used to
                             construct filters in the freq. plane.
   Lnorm            0        Optional integer indicating what norm the
                             filters should be normalized to.  A value of 1
                             will produce filters with the same L1 norm, 2
                             will produce filters with matching L2
                             norm. the default value of 0 results in no
                             normalization (the filters have unit height
                             Gaussian transfer functions on a log frequency
                             scale)
Returns:

  EO - 2D array of arrays of complex valued convolution results
       EO[s,o] = convolution result for scale s and orientation o.
       The real part is the result of convolving with the even
       symmetric filter, the imaginary part is the result from
       convolution with the odd symmetric filter.

       Hence:
       abs.(EO[s,o]) returns the magnitude of the convolution over the
                    image at scale s and orientation o.
       angle.(EO[s,o]) returns the phase angles.

  BP - Array of bandpass images corresponding to each scale s.
```

Notes on filter settings to obtain even coverage of the spectrum energy

```
dThetaOnSigma 1.2 - 1.3
sigmaOnf  .90   mult 1.15
sigmaOnf  .85   mult 1.2
sigmaOnf  .75   mult 1.4       (bandwidth ~1 octave)
sigmaOnf  .65   mult 1.7
sigmaOnf  .55   mult 2.2       (bandwidth ~2 octaves)
```

The determination of `mult` given `sigmaOnf` is entirely empirical.  What I do is plot out the sum of the squared filter amplitudes in the frequency domain and see how even the coverage of the spectrum is.  If there are concentric 'gaps' in the spectrum one needs to reduce mult and/or reduce `sigmaOnf` (which increases filter bandwidth)

If there are 'gaps' radiating outwards then one needs to reduce `dthetaOnSigma` (increasing angular bandwidth of the filters)
