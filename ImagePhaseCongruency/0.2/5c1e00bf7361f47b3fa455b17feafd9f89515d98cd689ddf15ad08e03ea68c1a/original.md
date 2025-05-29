Phase preserving wavelet image denoising.

```
Usage: cleanimage = ppdenoise(img,  nscale = 5, norient = 6,
                              mult = 2.5, minwavelength = 2, sigmaonf = 0.55,
                              dthetaonsigma = 1.0, k = 3, softness = 1.0)
Argument:
          img - Image to be processed (greyscale)

Keyword arguments:
        nscale - No of filter scales to use (5-7) - the more scales used
                 the more low frequencies are covered.
       norient - No of orientations to use (6)
          mult - Multiplying factor between successive scales  (2.5-3)
 minwavelength - Wavelength of smallest scale filter (2)
      sigmaonf - Ratio of the standard deviation of the Gaussian
                 describing the log Gabor filter's transfer function
                 in the frequency domain to the filter center frequency (0.55)
 dthetaonsigma - Ratio of angular interval between filter orientations
                 and the standard deviation of the angular Gaussian (1)
                 function used to construct filters in the freq. plane.
             k - No of standard deviations of noise to reject 2-3
      softness - Degree of soft thresholding (0-hard to 1-soft)
```

The convolutions are done via the FFT.  Many of the parameters relate to the specification of the filters in the frequency plane.  Most arguments do not need to be changed from the defaults and are mostly not that critical.  The main parameter that you may wish to play with is `k`, the number of standard deviations of noise to reject.
