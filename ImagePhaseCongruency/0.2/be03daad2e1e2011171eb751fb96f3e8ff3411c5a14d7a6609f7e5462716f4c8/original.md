Phase Preserving Dynamic Range Compression

Generates a series of dynamic range compressed images at different scales. This function is designed to reveal subtle features within high dynamic range images such as aeromagnetic and other potential field grids. Often this kind of data is presented using histogram equalisation in conjunction with a rainbow colourmap. A problem with histogram equalisation is that the contrast amplification of a feature depends on how commonly its data value occurs, rather than on the amplitude of the feature itself.

Phase Preserving Dynamic Range Compression allows subtle features to be revealed without these distortions. Perceptually important phase information is preserved and the contrast amplification of anomalies in the signal is purely a function of their amplitude. It operates as follows: first a highpass filter is applied to the data, this controls the desired scale of analysis. The 2D analytic signal of the data is then computed to obtain local phase and amplitude at each point in the image. The amplitude is attenuated by adding 1 and then taking its logarithm, the signal is then reconstructed using the original phase values.

```
Usage: dimg = ppdrc(img, wavelength; clip, n)

Arguments:     img - Image to be processed. A 2D array of Real or Gray elements.
        wavelength - Scalar value, or Vector, of wavelengths, in pixels, of
                     the cut-in frequencies to be used when forming the highpass
                     versions of the image.  Try a range of values starting
                     with, say, a wavelength corresponding to half the size
                     of the image and working down to something like 50
                     grid units.
Keyword arguments:
              clip - Percentage of output image histogram to clip.  Only a
                     very small value should be used, say 0.01 or 0.02, but
                     this can be beneficial.  Defaults to 0.01%
                 n - Order of the Butterworth high pass filter.  Defaults
                     to 2

Returns:      dimg - Array of the dynamic range reduced images.  If only
                     one wavelength is specified the image is returned
                     directly, and not as a one element array of image arrays.
```

Important: Scaling of the image affects the results.  If your image has values of order 1 or less it is useful to scale the image up a few orders of magnitude. The reason is that when the frequency amplitudes are attenuated we add one before taking the log to avoid obtaining negative results for values less than one.  Thus if `v` is small `log(1 + v)` will not be a good approximation to `log(v)`. However, if you scale the image by say, 1000 then `log(1 + 1000*v)` will be a reasonable approximation to `log(1000*v)`.

When specifying the array `wavelength` it is suggested that you use wavelengths that increase in a geometric series.  You can use the function `geoseries()` to conveniently do this

Example using `geoseries()` to generate a set of wavelengths that increase geometrically in 10 steps from 50 to 800.

```
   dimg = ppdrc(img, geoseries((50 800), 10))
```

See also: [`highpassmonogenic`](@ref), [`geoseries`](@ref)
