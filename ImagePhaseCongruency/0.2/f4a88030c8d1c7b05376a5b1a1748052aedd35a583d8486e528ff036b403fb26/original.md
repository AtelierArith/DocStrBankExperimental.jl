Compute phase and amplitude in highpass images via monogenic filters.

```
Usage: (phase, orient, E) = highpassmonogenic(img, maxwavelength, n)

Arguments:           img - Image to be processed.  A 2D array of Real or Gray elements.
           maxwavelength - Wavelength(s) in pixels of the  cut-in frequency(ies)
                           of the Butterworth highpass filter.
                       n - The order of the Butterworth filter. This is an
                           integer >= 1.  The higher the value the sharper
                           the cutoff.

Returns:           phase - The local phase. Values are between -pi/2 and pi/2
                  orient - The local orientation. Values between -pi and pi.
                           Note that where the local phase is close to
                           +-pi/2 the orientation will be poorly defined.
                       E - Local energy, or amplitude, of the signal.
```

Note that `maxwavelength` can be an array in which case the outputs will be an array of output images of length `nscales`,  where `nscales = length(maxwavelength)`.

See also: [`bandpassmonogenic`](@ref), [`ppdrc`](@ref), [`monofilt`](@ref)
